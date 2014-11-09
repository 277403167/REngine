REngine
=======

Rule Engine

AppSetting���ã�<br />
&nbsp;&nbsp;&nbsp;&nbsp;&lt;appSettings&gt;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;add key="XExtractor.RulefilesPath" value="E:\rules"/&gt;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&lt;add key="XExtractor.ThrowExceptionIfNotfoundRule" value="1"/&gt;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&lt;/appSettings&gt;<br />
	<br />
�����ļ�(*.rule)�������£�<br />
&nbsp;&nbsp;&nbsp;&nbsp;#region �ۿ۹���<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;rule default<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return 1;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;end rule<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;rule A��˾<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if(customerScore&gt;=0&&customerScore&lt;100)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return 1;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if(customerScore&gt;=100&&customerScore&lt;300)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return 0.8;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return 0.5;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;end rule<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;rule B��˾<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if(customerScore&gt;=0&&customerScore&lt;100)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return 0.9;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if(customerScore&gt;=100&&customerScore&lt;300)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return 0.7;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return 0.6;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;end rule<br />
&nbsp;&nbsp;&nbsp;&nbsp;#endregion<br />
			<br />
C#�������£�<br />
			XEngine.LoadSettings();<br />
			<br />
			Console.WriteLine("�ۿ۹��� - ��ʹ��");<br />
            {<br />
                var result = XEngine.InvokeAsFloat("�ۿ۹���", XEngine.CreateParameter("customerScore", 220));<br />
                Console.WriteLine("         " + result);<br />
            }<br />
			<br />
            Console.WriteLine("�ۿ۹��� - ���ֹ�˾ - A��˾");<br />
            {<br />
                var result = XEngine.InvokeAsFloat("�ۿ۹���", "A��˾", XEngine.CreateParameter("customerScore", 220));<br />
                Console.WriteLine("         " + result);<br />
            }<br />
			<br />
            Console.WriteLine("�ۿ۹��� - ���ֹ�˾ - B��˾");<br />
            {<br />
                var result = XEngine.InvokeAsFloat("�ۿ۹���", "B��˾", XEngine.CreateParameter("customerScore", 220));<br />
                Console.WriteLine("         " + result);<br />
            }<br />
			<br />
            Console.WriteLine("�ۿ۹��� - ���ֹ�˾ - C��˾");<br />
            {<br />
                var result = XEngine.InvokeAsFloat("�ۿ۹���", "C��˾", XEngine.CreateParameter("customerScore", 220));<br />
                Console.WriteLine("         " + result);<br />
            }<br />