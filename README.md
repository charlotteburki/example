# example

More than the modifications presentedn in the pull request I made other modifications just for my specific needs, that are not generalisable. I wanted to do a Independent Metropolis, so that my proposal distribution is uniform and do not dependent on the set of parameters. I did that by:

## 1. Create my own proposal distribution that I added in the metropolis.py file:

class UniformProposal2(Proposal):
    def __call__(self):
        t1=nr.uniform(low=-0.5,high=19.5,size=3)
        t2=nr.uniform(low=0.7,high=1,size=1)
        t3=nr.uniform(low=0.3,high=0.5,size=2)
        t1=np.append(t1,t2)
        t1=np.append(t1,t3)
        return t1
       
## 2. Use that distribution as default: 
So I modified line 115 to:

 self.proposal_dist = UniformProposal2(S)
 
## 3. Not taking into account the last set of parameters
at line 158: 
I modified that:
q = (q0 + delta)

to be just that:
q=delta
