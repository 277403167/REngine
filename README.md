REngine
=======

Rule Engine

AppSetting���ã�<br />
	<appSettings><br />
		<add key="XExtractor.RulefilesPath" value="E:\rules"/><br />
		<add key="XExtractor.ThrowExceptionIfNotfoundRule" value="1"/><br />
	</appSettings><br />
	<br />
�����ļ�(*.rule)�������£�<br />
			#region �ۿ۹���<br />
				rule default<br />
					return 1;<br />
				end rule<br />
				rule A��˾<br />
					if(customerScore>=0&&customerScore<100)<br />
						return 1;<br />
					if(customerScore>=100&&customerScore<300)<br />
						return 0.8;<br />
					return 0.5;<br />
				end rule<br />
				rule B��˾<br />
					if(customerScore>=0&&customerScore<100)<br />
						return 0.9;<br />
					if(customerScore>=100&&customerScore<300)<br />
						return 0.7;<br />
					return 0.6;<br />
				end rule<br />
			#endregion<br />
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