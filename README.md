REngine
=======

Rule Engine

AppSetting���ã�<br />
	&lt;appSettings&gt;
		<add key="XExtractor.RulefilesPath" value="E:\rules"/>
		<!--<add key="XExtractor.ThrowExceptionIfNotfoundRule" value="1"/>-->
	</appSettings>

�����ļ�(*.rule)�������£�
			#region �ۿ۹���
				rule default
					return 1;
				end rule
				rule A��˾
					if(customerScore>=0&&customerScore<100)
						return 1;
					if(customerScore>=100&&customerScore<300)
						return 0.8;
					return 0.5;
				end rule
				rule B��˾
					if(customerScore>=0&&customerScore<100)
						return 0.9;
					if(customerScore>=100&&customerScore<300)
						return 0.7;
					return 0.6;
				end rule
			#endregion

C#�������£�
			XEngine.LoadSettings();

			Console.WriteLine("�ۿ۹��� - ��ʹ��");
            {
                var result = XEngine.InvokeAsFloat("�ۿ۹���", XEngine.CreateParameter("customerScore", 220));
                Console.WriteLine("         " + result);
            }

            Console.WriteLine("�ۿ۹��� - ���ֹ�˾ - A��˾");
            {
                var result = XEngine.InvokeAsFloat("�ۿ۹���", "A��˾", XEngine.CreateParameter("customerScore", 220));
                Console.WriteLine("         " + result);
            }

            Console.WriteLine("�ۿ۹��� - ���ֹ�˾ - B��˾");
            {
                var result = XEngine.InvokeAsFloat("�ۿ۹���", "B��˾", XEngine.CreateParameter("customerScore", 220));
                Console.WriteLine("         " + result);
            }

            Console.WriteLine("�ۿ۹��� - ���ֹ�˾ - C��˾");
            {
                var result = XEngine.InvokeAsFloat("�ۿ۹���", "C��˾", XEngine.CreateParameter("customerScore", 220));
                Console.WriteLine("         " + result);
            }