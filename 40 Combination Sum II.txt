class Solution {
    List<List<Integer>>result=new ArrayList<>();
    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
        Arrays.sort(candidates);
        helper(candidates,0,new ArrayList<Integer>(),0,target);
        return result;
    }
    public void helper(int[] candidates, int position, List<Integer>input, int sum, int target)
    {
        if(sum==target)
        {
            result.add(input);
            return;
        }
        if(position>=candidates.length||sum>target)
            return;
        int prev=-1;
        for(int i=position;i<candidates.length;i++)
        {
            if(candidates[i]==prev)
                continue;
            prev=candidates[i];
            List<Integer>copy=new ArrayList<>(input);
            copy.add(candidates[i]);
            helper(candidates,i+1,copy,sum+candidates[i],target);
        }
    }
}