#css - grid 学习记录
##容器设置(container) 
*	display:grid;  
>行/列宽度设置
			grid-template-columns: 100px 30% 1fr;
			grid-template-rows: 50px 100px 50px 100px; 
			grid-template-rows: repeat(2,50px 100px); 
			grid-template-columns: repeat(auto-fill, 100px); 尽量一排占满 
			minmax(100px, 1fr)表示列宽不小于100px，不大于1fr 
			grid-template-columns: 100px auto 100px; auto即剩余宽度或高度 
            
*	>网格线名称
			grid-template-columns: [c1] 100px [c2] 100px [c3] auto [c4];
			grid-template-rows   : [r1] 100px [r2] 100px [r3] auto [r4]; 
            
*	>行间距
                row-gap: 20px;
                column-gap: 20px
                gap: <grid-row-gap> <grid-column-gap>;
            
*	>grid-template-areas 网格区域 
                网格布局允许指定"区域"（area），一个区域由单个或多个单元格组成。
                grid-template-areas: "header header header"
                                     "main main sidebar"
                                     "footer footer footer";
                某些区域不需要利用，则使用"点"（.）表示
                区域的命名会影响到网格线。每个区域的起始网格线，
                会自动命名为区域名-start，终止网格线自动命名为区域名-end
            
*	>grid-auto-flow 网格项排列顺序，默认先行后列
                grid-auto-flow: row  | column;
                还可以设成row dense(剩余的按照从左到右排列)和column dense(剩余的按照从上到下排列)
            
*	>单元格内容水平位置 -- justify-items
                    start：对齐单元格的起始边缘。
                    end：对齐单元格的结束边缘。
                    center：单元格内部居中。
                    stretch：拉伸，占满单元格的整个宽度（默认

*	>单元格内容垂直位置 -- align-items    
                    start：对齐单元格的起始边缘。
                    end：对齐单元格的结束边缘。
                    center：单元格内部居中。
                    stretch：拉伸，占满单元格的整个宽度（默认
                
*	>合并写法
                    place-items: <align-items> <justify-items>;
            
*	>整个内容区域在容器的位置摆放
			justify-content 水平
			align-content   垂直
				start - 对齐容器的起始边框。
				end - 对齐容器的结束边框。
				center - 容器内部居中。
				stretch - 项目大小没有指定时，拉伸占据整个网格容器。
				space-around - 每个项目两侧的间隔相等。所以，项目之间的间隔比项目与容器边框的间隔大一倍。
				space-between - 项目与项目的间隔相等，项目与容器边框之间没有间隔。
				space-evenly - 项目与项目的间隔相等，项目与容器边框之间也是同样长度的间隔。

			place-content属性是align-content属性和justify-content属性的合并简写形式。
			place-content: <align-content> <justify-content>
            
            
*	>超出的项
		grid-auto-rows: 50px;    本来只有9项三行三列，第十个行高为50
		grid-auto-columns: 30px; 本来只有9项三行三列，第十个列宽为30
				
## 项目设置(item) 
			
*	> 1、列线， 第一根 =》 第三根（行的写法一样）
			grid-column-start: 1;
			grid-column-end: 3;
					||
				VVVV  等价于
			grid-column: 1/3;
					||
				VVVV  等价于
			grid-column: 1/span 2(占据2格);
                    
*	>2、grid-column-start: span 2 === grid-column-end: span 2
*	>3、
		.item-1 {
			grid-column: 1; (1 / span 1 || 1 / 2)
			grid-row: 1;    (1 / span 1 || 1 / 2)
		}
*	>4、属性指定项目放在哪一个区域
			(1):.item-1 {
					grid-area: e; //放到命名为e的区域
				}
			(2):grid-area
				.item {
					grid-area: <row-start> / <column-start> / <row-end> / <column-end>;
					grid-area: 1 / 1 / 3 / 3; // 4根轴线围城的区域
				}
			(3):单个单元格内内容拜访效果
				justify-self属性设置单元格内容的水平位置（左中右）,跟justify-items属性的用法完全一致，但只作用于单个项目。
				align-self属性设置单元格内容的垂直位置（上中下）,跟align-items属性的用法完全一致，也是只作用于单个项目。
            
