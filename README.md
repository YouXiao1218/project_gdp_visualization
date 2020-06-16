# project_gdp_visualization
#coding:utf-8
"""
综合项目:世行历史数据基本分类及其可视化
作者：
日期

"""

import csv
import math
import pygal
import pygal_maps_world  #导入需要使用的库
from pyecharts.charts import Map
from pyecharts.globals import ChartType, SymbolType
from pyecharts.globals import ThemeType 
from pyecharts import options as opts
import random

def read_csv_as_nested_dict(filename, keyfield, separator, quote): #读取原始csv文件的数据，格式为嵌套字典
    """
    输入参数:
      filename:csv文件名
      keyfield:键名
      separator:分隔符
      quote:引用符

    输出:
      读取csv文件数据，返回嵌套字典格式，其中外层字典的键对应参数keyfiled，内层字典对应每行在各列所对应的具体值
    """
    result={}
    with open(filename,newline="")as csvfile:
        csvreader=csv.DictReader(csvfile,delimiter=separator,quotechar=quote)
        for row in csvreader:
            rowid=row[keyfield]
            result[rowid]=row
    return result
gdpcountries=read_csv_as_nested_dict(r"C:\Users\lblyz\Desktop\学习\computer_course\shi_yan\week12_python_csv2\综合项目\isp_gdp.csv", 'Country Code', ',', '"')
# print(gdpcountries)

pygal_countries = pygal.maps.world.COUNTRIES #读取pygal.maps.world中国家代码信息（为字典格式），其中键为pygal中各国代码，值为对应的具体国名(建议将其显示在屏幕上了解具体格式和数据内容）
# print(pygal_countries)
def reconcile_countries_by_name(plot_countries, gdp_countries): #返回在世行有GDP数据的绘图库国家代码字典，以及没有世行GDP数据的国家代码集合
	same=pygal_countries.keys()&gdpcountries.keys()
	dict1 = {key:pygal_countries[key] for key in pygal_countries.keys()}
	different=pygal_countries.keys() - gdpcountries.keys()
	set1=(different)
	sum=(dict1,set1)
	return sum
    # """
    
    # 输入参数:
    # plot_countries: 绘图库国家代码数据，字典格式，其中键为绘图库国家代码，值为对应的具体国名
    # gdp_countries:世行各国数据，嵌套字典格式，其中外部字典的键为世行国家代码，值为该国在世行文件中的行数据（字典格式)
    
    # 输出：
    # 返回元组格式，包括一个字典和一个集合。其中字典内容为在世行有GDP数据的绘图库国家信息（键为绘图库各国家代码，值为对应的具体国名),
    # 集合内容为在世行无GDP数据的绘图库国家代码
    # """
    # pass # 编码，结束后将pass删除
    # # 不要忘记返回结果
reconcile_countries_by_name(pygal_countries,gdpcountries)
    


def build_map_dict_by_name(gdpinfo, plot_countries, year):
	set_1=gdpcountries.keys() - pygal_countries.keys()
	
	q=pygal_countries.keys()
	for row1 in q:
		for row2 in set_1:
			dict2={}
			# math.log()
			dict2[pygal_countries[row1]]=gdpcountries[row2][year]
    
			set2=gdpcountries[row2][year]
			sum1=(set_1,set2,dict2)
	return sum1
	# """
    # 输入参数:
    # gdpinfo: gdp信息字典
	# plot_countries: 绘图库国家代码数据，字典格式，其中键为绘图库国家代码，值为对应的具体国名
	# year: 具体年份值
	
    # 输出：
    # 输出包含一个字典和二个集合的元组数据。其中字典数据为绘图库各国家代码及对应的在某具体年份GDP产值（键为绘图库中各国家代码，值为在具体年份（由year参数确定）所对应的世行GDP数据值。为
    # 后续显示方便，GDP结果需转换为以10为基数的对数格式，如GDP原始值为2500，则应为log2500，ps:利用math.log()完成)
    # 2个集合一个为在世行GDP数据中完全没有记录的绘图库国家代码，另一个集合为只是没有某特定年（由year参数确定）世行GDP数据的绘图库国家代码

   # """
    # pass # 编码，结束后将pass删除
    # # 不要忘记返回结果
	
# a=build_map_dict_by_name(gdpcountries, pygal_countries, '1970')


def render_world_map(gdpcountries, plot_countries, year, map_file): #将具体某年世界各国的GDP数据(包括缺少GDP数据以及只是在该年缺少GDP数据的国家)以地图形式可视化
	a=[]
	with open(r"C:\Users\lblyz\Desktop\学习\computer_course\shi_yan\week12_python_csv2\综合项目\isp_gdp.csv") as f:
		reader = csv.reader(f)
		header_row = next(reader)
		datas = []
		for row in reader:
			datas.append(row[0])
			for m in row[0]:
			# print(row[0])
				set_1=gdpcountries.keys() - pygal_countries.keys()
	
	q=pygal_countries.keys()
	for row2 in set_1:
		for row1 in q:	
			for y in range(1960,2017):
				# num=[1960,1961,1962,1963,1964,1965,1966,1967,1968,1969,1970,1971,1972,1973,1974,1975,1976,1977,1978,1979,1980,1981,1982,1983,1984,1985,1986,1987,1988,1989,1990,1991,33:1992,34:1993,35:1994,36:1995,37:1996,38:1997,39:1998,40:1999,41:2000,42:2001,43:2002,44:2003,45:2004,46:2005,47:2006,48:2007,49:2008,50:2009,51:2010,52:2011,53:2012,54:2013,55:2014
				# ,56:2015,57:2016]
				# w=str(gdpcountries[row2].keys())
				dict2={}
				dict3={}
				# math.log()
				dict2[row2]=gdpcountries[row2][year]
				set2=gdpcountries[row2][year]
				sum1=(set_1,set2,dict2)
				dict3[row2]=gdpcountries[row2][year]
				# print(dict3)
	# data1=[(" ",dict3[year])]
	# data2=[(" ",dict3[year])]
	# for b in row[0]:
		# locate=datas
		# print(locate)
		# list1=list(zip(locate,gdpcountries[row2][year])) #数据类型为元组列表，均可
		# list2=list(zip(locate,gdpcountries[row2][year]))
	wm = pygal.maps.world.World()
	wm.force_uri_protocol = 'http'
	wm.title = "世界地图"
	wm.add("缺少GDP数据", dict2)
	wm.add("只是在该年缺少GDP数据", dict3)
	wm.render_to_file(map_file)


	# c = (
		# Map(init_opts=opts.InitOpts(theme=ThemeType.SHINE))
			
			# .add("缺少GDP数据", list1,maptype="world")  # 这个数据是需要输入列表形式地图数据的，如[（'广东'，100）,（'江西'，100）]
			# .add("只是在该年缺少GDP数据", list2,maptype="world")
			# .set_series_opts(label_opts=opts.LabelOpts(is_show=False))
			# .set_global_opts(title_opts=opts.TitleOpts(title="世界地图"),
					# visualmap_opts=opts.VisualMapOpts(max_=100000000,min_=100,is_piecewise=True))

			# )
    # """
    # Inputs:
      
      # gdpinfo:gdp信息字典
      # plot_countires:绘图库国家代码数据，字典格式，其中键为绘图库国家代码，值为对应的具体国名
      # year:具体年份数据，以字符串格式程序，如"1970"
      # map_file:输出的图片文件名
    
    # 目标：将指定某年的世界各国GDP数据在世界地图上显示，并将结果输出为具体的的图片文件
    # 提示：本函数可视化需要利用pygal.maps.world.World()方法
     

    # """
    # pass #编码，结束后将pass删除
    # #不要忘记返回结果


def test_render_world_map(year):  #测试函数
    # """
    # 对各功能函数进行测试
    # """
    gdpinfo = {
        "gdpfile": "isp_gdp.csv",
        "separator": ",",
        "quote": '"',
        "min_year": 1960,
        "max_year": 2015,
        "country_name": "Country Name",
        "country_code": "Country Code"
    } #定义数据字典
  
   
    pygal_countries = pygal.maps.world.COUNTRIES   # 获得绘图库pygal国家代码字典

    # 测试时可以1970年为例，对函数继续测试，将运行结果与提供的svg进行对比，其它年份可将文件重新命名
    render_world_map(gdpcountries, pygal_countries, year, "isp_gdp_world_name_2000.svg")

    

    

# a=build_map_dict_by_name(gdpcountries, pygal_countries, '1970')


#程序测试和运行
print("欢迎使用世行GDP数据可视化查询")
print("----------------------")
year=input("请输入需查询的具体年份:")
test_render_world_map(year)
