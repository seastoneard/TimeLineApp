# TimeLineApp

<!-- Baidu Button END -->
<div id="article_content" class="article_content">

<p><span style="color:rgb(51,51,50); font-family:Arial,'Microsoft YaHei'; font-size:16px; line-height:26px">Android中使用RecyclerView实现时光轴，代码简单易懂.</span></p>
<p><span style="color:rgb(51,51,50); font-family:Arial,'Microsoft YaHei'; font-size:16px; line-height:26px"><br>
</span></p>
<p><span style="color:rgb(51,51,50); font-family:Arial,'Microsoft YaHei'; line-height:26px"><strong><span style="font-size:14px">效果如下：</span></strong></span></p>
<p><span style="color:rgb(51,51,50); font-family:Arial,'Microsoft YaHei'; font-size:16px; line-height:26px"><img src="http://img.blog.csdn.net/20170205140737547?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvemhoX2NzZG5fYXJk/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center" width="200" height="300" alt=""><br>
</span></p>
<p><span style="color:rgb(51,51,50); font-family:Arial,'Microsoft YaHei'; font-size:16px; line-height:26px"><br>
</span></p>
<p><span style="color:rgb(51,51,50); font-family:Arial,'Microsoft YaHei'; font-size:16px; line-height:26px"><span style="font-family:Arial; font-size:14px; line-height:26px">添加依赖(gradle中)：</span></span></p>
<p><pre name="code" class="java">compile 'com.android.support:recyclerview-v7:23.0.0'</pre><br>
<br>
<br>
<br>
</p>
<p><span style="color:rgb(51,51,50); font-family:Arial,'Microsoft YaHei'; line-height:26px"><strong><span style="font-size:14px">activity中：</span></strong></span></p>
<pre name="code" class="java" style="font-size: 16px;">public class MainActivity extends AppCompatActivity {

    private RecyclerView recyclerView;
    private List&lt;TimeInfo &gt; list=null;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        initLayout();
    }
    private void initLayout(){
        recyclerView= (RecyclerView) findViewById(R.id.recyclerView);
        recyclerView.setLayoutManager(new LinearLayoutManager(this));
        recyclerView.setHasFixedSize(true);
        recyclerView.setItemAnimator(new DefaultItemAnimator());
        list=new ArrayList&lt;&gt;();
        for(int i=0;i&lt;10;i++){
            list.add(new TimeInfo());
        }
        TimelineAdapter mAdapter = new TimelineAdapter(this, list);
        recyclerView.setAdapter(mAdapter);
    }
}</pre><strong><span style="font-size:14px">adapter中:</span></strong>
<p></p>
<p><span style="color:rgb(51,51,50); font-family:Arial,'Microsoft YaHei'; font-size:16px; line-height:26px"></span></p>
<pre name="code" class="java"><span style="font-size:18px;">public class TimelineAdapter extends  RecyclerView.Adapter&lt;TimelineAdapter.ViewHolder&gt; {

    private static final int ALPHA = 100;

    private List&lt;TimeInfo&gt; list=null;

    private Context context;
    public TimelineAdapter(Context context,List&lt;TimeInfo&gt; list) {
        this.list=list;
        this.context=context;

    }
    @Override
    public ViewHolder onCreateViewHolder(ViewGroup parent, int viewType) {
        View v = LayoutInflater.from(parent.getContext())
                .inflate(R.layout.v7_item_timeline, null);

        return new ViewHolder(v);
    }

    @Override
    public void onBindViewHolder(ViewHolder holder, int position) {
        holder.textView.setText(&quot;2016-08-10\n10：20&quot;);
        int color = context.getResources().getColor(R.color.colorAccent);
        holder.civ.setFillColor(color);
        holder.civ.setBorderColor(ColorUtils.setAlphaComponent(color, ALPHA));
        holder.img.setBackgroundResource(R.mipmap.ic_zhihu_logo);
        holder.item_timeline_view.setBackgroundResource(list.size()%2==0?R.color.colorAccent:R.color.colorPrimary);
    }

    @Override
    public int getItemCount() {
        return list.size();
    }


    public static class ViewHolder extends RecyclerView.ViewHolder {
        TextView textView;
        CircleImageView civ;
        ImageView img;
        View item_timeline_view;
        public ViewHolder(View v) {
            super(v);
            textView = (TextView) v.findViewById(R.id.item_timeline_time);
            civ= (CircleImageView) v.findViewById(R.id.item_timeline_icon_bg);
            img= (ImageView) v.findViewById(R.id.item_timeline_icon);
            item_timeline_view=v.findViewById(R.id.item_timeline_view);
        }
    }

}
</span></pre><span style="font-size:18px"><br>
</span>
<p><span style="font-size:18px"><a target="_blank" target="_blank" href="https://github.com/seastoneard/TimeLineApp">其他的代码见源码.....</a></span></p>
<p><br>
</p>
   
</div>

<!-- Baidu Button BEGIN -->

