# win10 PatchGuard ��̬����(btc�汾)  

**����Ŀ�ܹ���̬����pgContext��һ����**  
pgContext���ɶ���������    
0 - 0xc8��һ����    
0 - RtlMinimalBarrier��ƫ����һ����(��1803��,��ƫ��Ϊ0x1A2A8)    
RtlMinimalBarrier - RtlMinimalBarrier+0xA00 ������    
0x1A2A8+0xA00 - ....����һ�����ܵ�Context    
������Կ�doc�е�dump.log    
����Ŀ����0 - RtlMinimalBarrier��ƫ��    
���ڹ���PatchGuard,���ƫ���е������Ѿ��㹻    

## ԭ��

��ͨ���۲�dump.log�Ѿ����0x109�������ļ�,���Եó�һ����Ϣ    
��c8~RtlMinimalBarrier�����ݽ�β�󲿷���retΪ��β    
��retΪRtlMinimalBarrier����β������    

![pg](https://github.com/zhuhuibeishadiao/PatchGuardResearch/blob/master/doc/pg.PNG)    
��������ͨ��pgContext��ǰ2�����������ڴ���ײ���õ�pgContext���׵�ַ(ע��,��1809 rs5�汾��,rcx��ֵ�ı���)
Ȼ��ͨ���ҵ�δ���ܵ�RtlMinimalBarrier��ret,���н���.
ע��pgContext���ܴ��ڶ��,ʹ������ķ������ܲ���õ�ȫ����pgContext  

���µķ���:  
pgContext���ܲ�����ret��β  
�ھ������ʵ���ó����£�  
1.pgContext������ȫ���ܵ�(1909֮ǰ���ʽϵ� 1909������ʳ���)  
2.pgContext���ܻ�����NonPagedPoolSession���ڴ�(����ʱһ����Context�Ѿ����� �Ʋ��ʱpg���ڽ��н���)  
3.pgContext��β�����������������  
	��βΪc3  
	��βΪRtlMinimalBarrier����󼸸��ֽ�(Ŀǰ����1909ʵ�鷢�ֹ�)  
	���Ϊ����(RtlMinimalBarrier��������������)  
4.1909������ײ������pgContext���Ѿ���ȫ���ܺ��,�Ʋ�...  

��RtlMinimalBarrier������ŵĴ������ôһ���ṹ  
  
xxxxxxxxxxxxxxxxx  �����������������һ��  
ffffa38a`2cf1dc45  00000000`00000000  
ffffa38a`2cf1dc4d  fffff806`20cbe8c7 nt!ExQueueWorkItem+0x7  
ffffa38a`2cf1dc55  56d15c8b`00000010  
ffffa38a`2cf1dc5d  00000000`00000001  
ffffa38a`2cf1dc65  00000000`00000000  
ffffa38a`2cf1dc6d  00000000`00000000  
ffffa38a`2cf1dc75  00000000`00000000  
ffffa38a`2cf1dc7d  fffff806`20cbe8d7 nt!ExQueueWorkItem+0x17  
ffffa38a`2cf1dc85  2ecc050e`0000008a  
   
c3�����0���������ڶ���?  
            ʣ�µĽṹ��  
            _struct xxxxx  
            {
                PVOID routine;  
                ULONG checksum?;  
                ULONG routineCodeSize;  
                PVOID unknow;(һֱΪ1)  
                PVOID Fileds[3];  
            }  
  

## ���ڵ���PatchGuard  
˫�����ԣ���������ģʽ��,����,��Ҫ��windbg,�ȴ���������ȦȦ����,����תһ��,����תһ���ͻȻ��ס��ת��,��1-2�뿪��windbg����.  

## ����Ŀ�ݲ�����PatchGuard    
��ʵ,���˽���֮�����Ѿ�����������.    
ֻ��Ŀǰ���Ĳ����ڹ���,����.  

## Ŀ¼˵��  
doc:һЩ��������  
helper:���ڸ���dump��У��pgContext  
PatchGuard:���߼�  

## ��л
[tandasat : some-tips-to-analyze-patchguard](http://standa-note.blogspot.com/2015/10/some-tips-to-analyze-patchguard.html)  
[tandasat : findpg](https://github.com/tandasat/findpg)  
[tandasat : PgResarch](https://github.com/tandasat/PgResarch)  
mengwuji : windows10 patchguard�ƹ�����      
mengwuji : �ƹ�windows10 patchguardԭ����ʵ��      
[9176324 : Shark](https://github.com/9176324/Shark)  
[DarthTon : Blackbone](https://github.com/DarthTon/Blackbone)    
Mr Guo      


