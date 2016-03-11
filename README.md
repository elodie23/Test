# EXERCISES PYTHON - PART 1


# Exercice A - Match ends
# Given a list of strings, return Nb strings with length>=2 and 1st and last character are the same

def match_ends(words):
    Nb=0
    for word in words:
        if len(word)>=2 and word[0] in word[-1]:    
           Nb=Nb+1
    return Nb

# Test
#listeA = ['chienc','chatc','crocodilec']
#print match_ends(listeA)



# Exercice B - Front X
# Given a list of strings, return list with sorted order, except group strings beginning with 'x' first.
# Example: ['mix', 'xyz', 'apple', 'xanadu', 'aardvark']
# Result:['xanadu', 'xyz', 'aardvark', 'apple', 'mix']

def front_x(words):
   ct1=[]
   ct2=[]
   for word in words:
       if word[0] in "x":
           ct1.append(word)
       else:
           ct2.append(word)
   ct1.sort()
   ct2.sort()
   ct3=ct1+ct2
   return ct3

#Test
#listeB=['poire', 'banane', 'abricot', 'ananas', 'xili']
#print front_x(listeB)




# Exercice C - Sort Last
# Given a list of non-empty tuples, return a list sorted in increasing order by the last element in each tuple.
# e.g. [(1, 7), (1, 3), (3, 4, 5), (2, 2)]
# yields [(2, 2), (1, 3), (3, 4, 5), (1, 7)]
# Hint: use a custom key= function to extract the last element form each tuple

def sort_last(tuples):

   Liste_interm=[]
   for mot in tuples:
       Liste_interm.append(mot[-1])
   Liste_interm.sort()

   inter=[]
   for i in xrange(0, len(tuples)):
       for mot in tuples:
          if mot[-1]==Liste_interm[i]:
              inter.append(mot)
   return inter            

#Test
# ListeC=[(1, 7), (1, 3), (3, 4, 5), (2, 2)]
# print sort_last(ListeC)


    
    
    
# Exercice D - Remove Adjacent
# Given a list of numbers, return a list where all adjacent == elements 
# have been reduced to a single element
# Example: [1, 2, 2, 3] returns [1, 2, 3]
# Hint: You may create a new list or modify the passed in list.

def remove_adjacent(nums):

    inter=[]
    for i in xrange(0,len(nums)-1):
        if nums[i]==nums[i+1]:
             inter.append(nums[i])

    for j in xrange(0, len(inter)):
        nums.remove(inter[j])
    
    return nums
   
# Test    
# ListeD=[1,2,2,3,3,3,3,7,9,9]
# print remove_adjacent(ListeD)

    
    
    
    
# Exercice E - Linear Merge
# Given two lists sorted in increasing order, create and return a merged list
# of all the elements in sorted order. 
# Hint: You may modify the passed in lists.
# Ideally, the solution should work in "linear" time, making a single pass of both lists

def linear_merge(list1, list2):
   list3=list1+list2
   list3.sort()
   return list3

#Test
# ListeE1=[1,3,5,7,9]
# ListeE2=[2,4,6]
# print linear_merge(ListeE1, ListeE2)






# EXERCISES PYTHON - PART 2


# Exercice A - Donuts
# Given an int count of Nb donuts, return a string of the form 
# 'Number of donuts: ', where is the number passed in. 
# If >=10, then use the word 'many' instead of the actual count
# Donuts(5) returns 'Number of donuts: 5' / donuts(23) returns 'Number of donuts: many'


def donuts(count):
   s=str() 
   if count>=10:
       s='Number of donuts: many'
   else:
       s='Number of donuts: ' + str(count)
   return s

#Test   
# donuts1=12
# donuts2=7
# print donuts(donuts1)
# print donuts(donuts2)


# Exercice B - Both-ends
# Given a string s, return a string made of the first 2 and last 2 chars
# 'spring' yields 'spng'
# if length < 2, return instead the empty string

def both_ends(s):
    s2=str()
    if len(s)<2:
        s2=str()
    else:
        s2=str(s[0])+str(s[1])+str(s[-2])+str(s[-1])
    return s2

# Test
# s='spring'
# print both_ends(s)



# Exercice C - Fix-start
# Given a string s, return a string where all occurences of its first char
# have been changed to '*', except do not change the first char itself.
# 'babble' yields 'ba**le'
# Assume that the string is length 1 or more
# Hint: s.replace(stra, strb) returns a version of string s where all instances of stra have been replaced by strb.

def fix_start(s):
    s1=s[1:]
    s2=s[0]+s1.replace(s[0],'*')
    return s2
    
# Test
# s='babble'
# print fix_start(s)



# Exercice D - Mix Up
# Given strings a and b, return a single string with a and b separated by a space
# '<a> <b>', except swap the first 2 chars of each string
# 'mix', pod' -> 'pox mid'
# 'dog', 'dinner' -> 'dig donner'
# Assume a and b are length 2 or more.

def mix_up(a, b):
    a1=a.replace(a[0],b[0])
    a2=a1.replace(a1[1],b[1])
    b1=b.replace(b[0],a[0])
    b2=b1.replace(b1[1],a[1])
    c=a2+" "+b2
    return c

# Test
# a='mix'
# b='pod'
# print mix_up(a,b)



# TEST DE VALIDITE GLOBAL

def test(got, expected):
    if got == expected:
        prefix = ' OK '
    else:
        prefix = '  X '
    print '%s got: %s expected: %s' % (prefix, repr(got), repr(expected))
    
def main():
    print 'match_ends'
    test(match_ends(['aba', 'xyz', 'aa', 'x', 'bbb']), 3)
    test(match_ends(['', 'x', 'xy', 'xyx', 'xx']), 2)
    test(match_ends(['aaa', 'be', 'abc', 'hello']), 1)

    print
    print 'front_x'
    test(front_x(['bbb', 'ccc', 'axx', 'xzz', 'xaa']),
        ['xaa', 'xzz', 'axx', 'bbb', 'ccc'])
    test(front_x(['ccc', 'bbb', 'aaa', 'xcc', 'xaa']),
        ['xaa', 'xcc', 'aaa', 'bbb', 'ccc'])
    test(front_x(['mix', 'xyz', 'apple', 'xanadu', 'aardvark']),
        ['xanadu', 'xyz', 'aardvark', 'apple', 'mix'])
        
    print 'remove_adjacent'
    test(remove_adjacent([1, 2, 2, 3]), [1, 2, 3])
    test(remove_adjacent([2, 2, 3, 3, 3]), [2, 3])
    test(remove_adjacent([]), [])

    print
    print 'linear_merge'
    test(linear_merge(['aa', 'xx', 'zz'], ['bb', 'cc']),
        ['aa', 'bb', 'cc', 'xx', 'zz'])
    test(linear_merge(['aa', 'xx'], ['bb', 'cc', 'zz']),
        ['aa', 'bb', 'cc', 'xx', 'zz'])
    test(linear_merge(['aa', 'aa'], ['aa', 'bb', 'bb']),
        ['aa', 'aa', 'aa', 'bb', 'bb'])

    print 'donuts'
    test(donuts(4), 'Number of donuts: 4')
    test(donuts(9), 'Number of donuts: 9')
    test(donuts(10), 'Number of donuts: many')
    test(donuts(99), 'Number of donuts: many')

    print
    print 'both_ends'
    test(both_ends('spring'), 'spng')
    test(both_ends('Hello'), 'Helo')
    test(both_ends('a'), '')
    test(both_ends('xyz'), 'xyyz')
  
    print
    print 'fix_start'
    test(fix_start('babble'), 'ba**le')
    test(fix_start('aardvark'), 'a*rdv*rk')
    test(fix_start('google'), 'goo*le')
    test(fix_start('donut'), 'donut')

    print
    print 'mix_up'
    test(mix_up('mix', 'pod'), 'pox mid')
    test(mix_up('dog', 'dinner'), 'dig donner')
    test(mix_up('gnash', 'sport'), 'spash gnort')
    test(mix_up('pezzy', 'firm'), 'fizzy perm')
      
main()
