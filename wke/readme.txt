vs2015
 std::tr1::has_trivial_destructor -> std::is_trivially_default_constructible



old fix 
	add 
		DerivedNames.cpp
		DerivedResources.cpp
		DerivedCSSResources.cpp
		DerivedSVGResources.cpp
		DerivedMathMLResources.cpp

1>WebCore.lib(JSBindingsAllInOne.obj) : error LNK2001: �޷��������ⲿ���� "class WebCore::JSDOMWrapper * __cdecl WebCore::createJSSVGWrapper(class JSC::ExecState *,class WebCore::JSDOMGlobalObject *,class WTF::PassRefPtr<class WebCore::SVGElement>)" (?createJSSVGWrapper@WebCore@@YAPAVJSDOMWrapper@1@PAVExecState@JSC@@PAVJSDOMGlobalObject@1@V?$PassRefPtr@VSVGElement@WebCore@@@WTF@@@Z)

	add to DerivedSources.cpp 
	\wke_release\obj\WebCore\DerivedSources\JSSVGElementWrapperFactory.cpp(598): JSDOMWrapper* createJSSVGWrapper(ExecState* exec, JSDOMGlobalObject* globalObject, PassRefPtr<SVGElement> element)
	or diable Scalable Vector Graphics (SVG) 
		add #define ENABLE_SVG 0
		change \WebKitLibraries\win\tools\props\FeatureDefinesCairo.props(50):     <ENABLE_SVG />

project wtf:
	ignore WTF_USE_ICU_UNICODE
		open \Source\JavaScriptCore\wtf\unicode\icu\CollatorICU.cpp
		add
		#undef UCONFIG_NO_COLLATION
		#define UCONFIG_NO_COLLATION 1

project WebCore:
	ignore WTF_USE_ICU_UNICODE
		open \Source\WebCore\editing\TextIterator.cpp
		add
		#undef UCONFIG_NO_COLLATION
		#define UCONFIG_NO_COLLATION 1

all project:
	PTW32_STATIC_LIB
	CURL_STATICLIB
	LIBXML_STATIC
	JS_NO_EXPORT
	U_STATIC_IMPLEMENTATION

	release:
		_NDEBUG
		NDEBUG
		ignore DEBUG_ALL

WebCore:
	WTF_USE_EXPORT_MACROS

1>WebCore.lib(ResourceHandleCurl.obj) : warning LNK4217: ���ض���ķ��� _curl_slist_free_all �ں��� "public: __thiscall WebCore::ResourceHandleInternal::~ResourceHandleInternal(void)" (??1ResourceHandleInternal@WebCore@@QAE@XZ) �е���
1>WebCore.lib(ResourceHandleCurl.obj) : warning LNK4217: ���ض���ķ��� _curl_easy_pause �ں��� "private: void __thiscall WebCore::ResourceHandle::platformSetDefersLoading(bool)" (?platformSetDefersLoading@ResourceHandle@WebCore@@AAEX_N@Z) �е���

��δ����2>  CachedResource.cpp
2>E:\Microsoft Visual Studio 12.0\VC\include\utility(157): warning C4244: ����ʼ����: �ӡ�int��ת������float�������ܶ�ʧ���� (..\Source\WebCore\loader\cache\CachedImage.cpp)
2>          ..\Source\WebCore\loader\cache\CachedImage.cpp(121): �μ������ڱ���ĺ��� ģ�� ʵ������std::pair<WebCore::Image *,float>::pair<WebCore::Image*,int,void>(std::pair<WebCore::Image *,int> &&)��������
2>          ..\Source\WebCore\loader\cache\CachedImage.cpp(121): �μ������ڱ���ĺ��� ģ�� ʵ������std::pair<WebCore::Image *,float>::pair<WebCore::Image*,int,void>(std::pair<WebCore::Image *,int> &&)��������
2>  CachedResourceHandle.cpp


1>..\Source\JavaScriptCore\wtf\Assertions.cpp(31): warning C4068: δ֪����ע

6>d:\release_cairo_cflite\include\webcore\CSSWrapShapes.h : warning C4819: ���ļ����������ڵ�ǰ����ҳ(936)�б�ʾ���ַ����뽫���ļ�����Ϊ Unicode ��ʽ�Է�ֹ���ݶ�ʧ

5>d:\release_cairo_cflite\obj\webcore\derivedsources\jshtmlparamelement.cpp(91): fatal error C1128: �������������ļ���ʽ����: ��ʹ�� /bigobj ���б���

5>..\Source\WebCore\rendering\RenderRegion.cpp : warning C4819: ���ļ����������ڵ�ǰ����ҳ(936)�б�ʾ���ַ����뽫���ļ�����Ϊ Unicode ��ʽ�Է�ֹ���ݶ�ʧ

5>d:\wke\wke-master-ui\source\webcore\rendering\RenderThemeWin.h(29): fatal error C1017: ��Ч�������������ʽ

5>..\Source\WebCore\rendering\RenderFlowThread.cpp : warning C4819: ���ļ����������ڵ�ǰ����ҳ(936)�б�ʾ���ַ����뽫���ļ�����Ϊ Unicode ��ʽ�Է�ֹ���ݶ�ʧ

5>..\Source\WebCore\platform\win\PopupMenuWin.cpp(741): error C2065: ��CS_DROPSHADOW��: δ�����ı�ʶ��

5>..\Source\WebCore\css\CSSRegionStyleRule.cpp : warning C4819: ���ļ����������ڵ�ǰ����ҳ(936)�б�ʾ���ַ����뽫���ļ�����Ϊ Unicode ��ʽ�Է�ֹ���ݶ�ʧ

3>D:\wke\wke-master-ui\vs2008\props\WebCoreGeneratedCairo.props(4,5): warning MSB4011: �޷��ٴε��롰D:\wke\wke-master-ui\vs2008\props\common.props�����������ڡ�D:\wke\wke-master-ui\vs2008\props\WebCoreGeneratedCommon.props (4,5)���������������ܿ��������ɴ������󡣽����Դ˺������롣[D:\wke\wke-master-ui\vs2008\WebCoreGenerated.vcxproj]


3>D:\wke\wke-master-ui\Source\JavaScriptCore\wtf/MathExtras.h(144): error C2084: ������bool signbit(double)����������
3>          E:\Microsoft Visual Studio 12.0\VC\include\math.h(324) : �μ���signbit����ǰһ������
3>D:\wke\wke-master-ui\Source\JavaScriptCore\wtf/MathExtras.h(282): error C2264: ��signbit��: ����������������д���δ
���ú���

3>..\Source\JavaScriptCore\API\JSBase.cpp(91): warning C4273: ��JSGarbageCollect��: dll ���Ӳ�һ��
3>          d:\wke\wke-master-ui\source\javascriptcore\api\JSBase.h(132) : �μ���JSGarbageCollect����ǰһ������

include\private\javascriptcore\StringImpl.h(195): warning C4291: ��void *WTF::StringImpl::operator new(size_t,void *)��: δ�ҵ�ƥ���ɾ��������������ʼ�������쳣���򲻻��ͷ��ڴ�

5>D:\wke_release\include\private\JavaScriptCore/BumpPointerAllocator.h(124): warning C4291: ��void *WTF::BumpPointerPool::operator new(size_t,const WTF::PageAllocation &)��: δ�ҵ�ƥ���ɾ��������������ʼ�������쳣���򲻻��ͷ��ڴ�





http://blog.csdn.net/saga1979/article/details/41959197
https://qt.gitorious.org/qt/qt/commit/1bed55097b22f2071af71ebefc9897816977fd14
http://stackoverflow.com/questions/12113400/compiling-qt-4-8-x-for-visual-studio-2012/13085842#13085842

5>d:\release_cairo_cflite\include\private\javascriptcore\HashSet.h(180): error C2664: ��std::pair<WTF::HashTableConstIteratorAdapter<WTF::HashTable<int,int,WTF::IdentityExtractor<int>,WTF::IntHash<unsigned int>,WTF::HashTraits<Second>,WTF::HashTraits<Second>>,int>,bool>::pair(const std::pair<WTF::HashTableConstIteratorAdapter<WTF::HashTable<int,int,WTF::IdentityExtractor<int>,WTF::IntHash<unsigned int>,WTF::HashTraits<Second>,WTF::HashTraits<Second>>,int>,bool> &)��: �޷������� 1 �ӡ�std::pair<WTF::HashTableIterator<Key,Value,Extractor,HashFunctions,Traits,KeyTraits>,bool>��
ת��Ϊ��const std::pair<WTF::HashTableConstIteratorAdapter<WTF::HashTable<int,int,WTF::IdentityExtractor<int>,WTF::IntHash<unsigned int>,WTF::HashTraits<Second>,WTF::HashTraits<Second>>,int>,bool> &��
5>          with
5>          [
5>              Second=int
5>          ]
5>          and
5>          [
5>              Key=int
5>  ,            Value=int
5>  ,            Extractor=WTF::IdentityExtractor<int>
5>  ,            HashFunctions=WTF::IntHash<unsigned int>
5>  ,            Traits=WTF::HashTraits<int>
5>  ,            KeyTraits=WTF::HashTraits<int>
5>          ]
5>          and
5>          [
5>              Second=int
5>          ]
5>          ԭ������:  �޷��ӡ�std::pair<WTF::HashTableIterator<Key,Value,Extractor,HashFunctions,Traits,KeyTraits>,bool>��ת��Ϊ��const std::pair<WTF::HashTableConstIteratorAdapter<WTF::HashTable<int,int,WTF::IdentityExtractor<int>,WTF::IntHash<unsigned int>,WTF::HashTraits<Second>,WTF::HashTraits<Second>>,int>,bool>��
5>          with
5>          [
5>              Key=int
5>  ,            Value=int
5>  ,            Extractor=WTF::IdentityExtractor<int>
5>  ,            HashFunctions=WTF::IntHash<unsigned int>
5>  ,            Traits=WTF::HashTraits<int>
5>  ,            KeyTraits=WTF::HashTraits<int>
5>          ]
5>          and
5>          [
5>              Second=int
5>          ]
5>          û�п�����ִ�и�ת�����û������ת��������������޷����ø������
5>          d:\release_cairo_cflite\include\private\javascriptcore\HashSet.h(179): ������ ģ�� ��Ա������std::pair<WTF::HashTableConstIteratorAdapter<WTF::HashTable<int,int,WTF::IdentityExtractor<int>,WTF::IntHash<unsigned int>,WTF::HashTraits<Second>,WTF::HashTraits<Second>>,int>,bool> WTF::HashSet<int,WTF::DefaultHash<int>::Hash,WTF::HashTraits<Second>>::add(const int &)��ʱ
5>          with
5>          [
5>              Second=int
5>          ]
5>          ..\Source\WebCore\css\CSSMutableStyleDeclaration.cpp(832): �μ������ڱ���ĺ��� ģ�� ʵ������std::pair<WTF::HashTableConstIteratorAdapter<WTF::HashTable<int,int,WTF::IdentityExtractor<int>,WTF::IntHash<unsigned int>,WTF::HashTraits<Second>,WTF::HashTraits<Second>>,int>,bool> WTF::HashSet<int,WTF::DefaultHash<int>::Hash,WTF::HashTraits<Second>>::add(const int &)��������
5>          with
5>          [
5>              Second=int
5>          ]
5>          ..\Source\WebCore\css\CSSMutableStyleDeclaration.cpp(830): �μ������ڱ������ ģ�� ʵ������WTF::HashSet<int,WTF::DefaultHash<int>::Hash,WTF::HashTraits<Second>>��������
5>          with
5>          [
5>              Second=int
5>          ]







5>  DatabaseTracker.cpp
5>E:\Microsoft Visual Studio 12.0\VC\include\utility(183): warning C4503: ��WTF::HashTable<WTF::RefPtr<WebCore::SecurityOrigin>,std::pair<WTF::RefPtr<WebCore::SecurityOrigin>,WTF::HashMap<WTF::String,WebCore::DatabaseTracker::DatabaseSet *,WTF::DefaultHash<WTF::String>::Hash,WTF::HashTraits<WTF::String>,WTF::HashTraits<MappedArg>> >,WTF::PairFirstExtractor<std::pair<WTF::RefPtr<WebCore::SecurityOrigin>,WTF::HashMap<WTF::String,MappedArg,WTF::DefaultHash<WTF::String>::Hash,WTF::HashTraits<WTF::String>,WTF::HashTraits<MappedArg>> >>,WebCore::SecurityOriginHash,WTF::PairHashTraits<WTF::HashTraits<KeyArg>,WTF::HashTraits<WTF::HashMap<WTF::String,MappedArg,WTF::DefaultHash<WTF::String>::Hash,WTF::HashTraits<WTF::String>,WTF::HashTraits<MappedArg>>>>,WTF::HashTraits<KeyArg>>::add��: �����������ĳ��ȣ����Ʊ��ض�
5>          with
5>          [
5>              MappedArg=WebCore::DatabaseTracker::DatabaseSet *
5>  ,            KeyArg=WTF::RefPtr<WebCore::SecurityOrigin>
5>          ]
5>E:\Microsoft Visual Studio 12.0\VC\include\utility(183): warning C4503: ��std::pair<WTF::HashTableIteratorAdapter<WTF::HashTable<WTF::RefPtr<WebCore::SecurityOrigin>,std::pair<WTF::RefPtr<WebCore::SecurityOrigin>,WTF::HashMap<WTF::String,WebCore::DatabaseTracker::DatabaseSet *,WTF::DefaultHash<WTF::String>::Hash,WTF::HashTraits<WTF::String>,WTF::HashTraits<MappedArg>> >,WTF::PairFirstExtractor<std::pair<WTF::RefPtr<WebCore::SecurityOrigin>,WTF::HashMap<WTF::String,MappedArg,WTF::DefaultHash<WTF::String>::Hash,WTF::HashTraits<WTF::String>,WTF::HashTraits<MappedArg>> >>,WebCore::SecurityOriginHash,WTF::PairHashTraits<WTF::HashTraits<KeyArg>,WTF::HashTraits<WTF::HashMap<WTF::String,MappedArg,WTF::DefaultHash<WTF::String>::Hash,WTF::HashTraits<WTF::String>,WTF::HashTraits<MappedArg>>>>,WTF::HashTraits<KeyArg>>,std::pair<WTF::RefPtr<WebCore::SecurityOrigin>,WTF::HashMap<WTF::String,MappedArg,WTF::DefaultHash<WTF::String>::Hash,WTF::HashTraits<WTF::String>,WTF::HashTraits<MappedArg>> >>,bool>::pair��: �����������ĳ��ȣ����Ʊ��ض�
5>          with
5>          [
5>              MappedArg=WebCore::DatabaseTracker::DatabaseSet *
5>  ,            KeyArg=WTF::RefPtr<WebCore::SecurityOrigin>
6>d:\release_cairo_cflite\include\webcore\CSSWrapShapes.h : warning C4819: ���ļ����������ڵ�ǰ����ҳ(936)�б�ʾ���ַ����뽫���ļ�����Ϊ Unicode ��ʽ�Է�ֹ���ݶ�ʧ
6>D:\wke_release\Include\WebCore/RenderThemeWin.h(29): fatal error C1017: ��Ч�������������ʽ

6>d:\release_cairo_cflite\include\webcore\CSSWrapShapes.h : warning C4819: ���ļ����������ڵ�ǰ����ҳ(936)�б�ʾ���ַ����뽫���ļ�����Ϊ Unicode ��ʽ�Է�ֹ���ݶ�ʧ

5>          ]
5>E:\Microsoft Visual Studio 12.0\VC\include\utility(183): warning C4503: ��WTF::addIterator��: �����������ĳ��ȣ����Ʊ��ض�
5>E:\Microsoft Visual Studio 12.0\VC\include\utility(183): warning C4503: ��std::make_pair��: �����������ĳ��ȣ����Ʊ��ض�
5>E:\Microsoft Visual Studio 12.0\VC\include\utility(183): warning C4503: ��std::pair<WTF::HashTableIterator<Key,Value,Extractor,HashFunctions,Traits,KeyTraits>,bool>::pair��: �����������ĳ��ȣ����Ʊ��ض�
5>          with
5>          [
5>              Key=WTF::RefPtr<WebCore::SecurityOrigin>
5>  ,            Value=std::pair<WTF::RefPtr<WebCore::SecurityOrigin>,WTF::HashMap<WTF::String,WebCore::DatabaseTracker::DatabaseSet *,WTF::DefaultHash<WTF::String>::Hash,WTF::HashTraits<WTF::String>,WTF::HashTraits<WTF::HashSet<WebCore::AbstractDatabase *,WTF::PtrHash<WebCore::AbstractDatabase *>,WTF::HashTraits<WebCore::AbstractDatabase *>> *>> *>
5>  ,            Extractor=WTF::PairFirstExtractor<std::pair<WTF::RefPtr<WebCore::SecurityOrigin>,WTF::HashMap<WTF::String,WebCore::DatabaseTracker::DatabaseSet *,WTF::DefaultHash<WTF::String>::Hash,WTF::HashTraits<WTF::String>,WTF::HashTraits<WTF::HashSet<WebCore::AbstractDatabase *,WTF::PtrHash<WebCore::AbstractDatabase *>,WTF::HashTraits<WebCore::AbstractDatabase *>> *>> *>>
5>  ,            HashFunctions=WebCore::SecurityOriginHash
5>  ,            Traits=WTF::PairHashTraits<WTF::HashTraits<WTF::RefPtr<WebCore::SecurityOrigin>>,WTF::HashTraits<WTF::HashMap<WTF::String,WebCore::DatabaseTracker::DatabaseSet *,WTF::DefaultHash<WTF::String>::Hash,WTF::HashTraits<WTF::String>,WTF::HashTraits<WTF::HashSet<WebCore::AbstractDatabase *,WTF::PtrHash<WebCore::AbstractDatabase *>,WTF::HashTraits<WebCore::AbstractDatabase *>> *>> *>>
5>  ,            KeyTraits=WTF::HashTraits<WTF::RefPtr<WebCore::SecurityOrigin>>
5>          ]
5>  IDBAny.cpp











compile wke:
1>WebCore.lib(Frame.obj) : error LNK2001: �޷��������ⲿ���� "void __cdecl WebCore::WebKitFontFamilyNames::init(void)" (?init@WebKitFontFamilyNames@WebCore@@YAXXZ)
1>WebCore.lib(Frame.obj) : error LNK2001: �޷��������ⲿ���� "void __cdecl WebCore::HTMLNames::init(void)" (?init@HTMLNames@WebCore@@YAXXZ)
1>WebCore.lib(Frame.obj) : error LNK2001: �޷��������ⲿ���� "void __cdecl WebCore::XMLNSNames::init(void)" (?init@XMLNSNames@WebCore@@YAXXZ)
1>WebCore.lib(Frame.obj) : error LNK2001: �޷��������ⲿ���� "void __cdecl WebCore::XMLNames::init(void)" (?init@XMLNames@WebCore@@YAXXZ)
1>WebCore.lib(Frame.obj) : error LNK2001: �޷��������ⲿ���� "void __cdecl WebCore::MathMLNames::init(void)" (?init@MathMLNames@WebCore@@YAXXZ)
1>WebCore.lib(Frame.obj) : error LNK2001: �޷��������ⲿ���� "void __cdecl WebCore::SVGNames::init(void)" (?init@SVGNames@WebCore@@YAXXZ)
1>WebCore.lib(Frame.obj) : error LNK2001: �޷��������ⲿ���� "void __cdecl WebCore::XLinkNames::init(void)" (?init@XLinkNames@WebCore@@YAXXZ)
1>WebCore.lib(EditingAllInOne.obj) : error LNK2001: �޷��������ⲿ���� _ucol_getStrength_4_0
1>WebCore.lib(EditingAllInOne.obj) : error LNK2001: �޷��������ⲿ���� _ucol_setStrength_4_0
1>WebCore.lib(EditingAllInOne.obj) : error LNK2001: �޷��������ⲿ���� _usearch_open_4_0
1>WebCore.lib(EditingAllInOne.obj) : error LNK2001: �޷��������ⲿ���� _usearch_setOffset_4_0
1>WebCore.lib(EditingAllInOne.obj) : error LNK2001: �޷��������ⲿ���� _usearch_getMatchedLength_4_0
1>WebCore.lib(EditingAllInOne.obj) : error LNK2001: �޷��������ⲿ���� _usearch_setText_4_0
1>WebCore.lib(EditingAllInOne.obj) : error LNK2001: �޷��������ⲿ���� _usearch_getCollator_4_0
1>WebCore.lib(EditingAllInOne.obj) : error LNK2001: �޷��������ⲿ���� _usearch_setPattern_4_0
1>WebCore.lib(EditingAllInOne.obj) : error LNK2001: �޷��������ⲿ���� _usearch_next_4_0
1>WebCore.lib(EditingAllInOne.obj) : error LNK2001: �޷��������ⲿ���� _usearch_reset_4_0
1>WebCore.lib(ScriptValue.obj) : error LNK2001: �޷��������ⲿ���� __imp__JSValueIsEqual1>WebCore.lib(CSSParser.obj) : error LNK2001: �޷��������ⲿ���� "struct WebCore::Property const * __cdecl WebCore::findProperty(char const *,unsigned int)" (?findProperty@WebCore@@YAPBUProperty@1@PBDI@Z)
1>WebCore.lib(CSSParser.obj) : error LNK2001: �޷��������ⲿ���� "struct WebCore::Value const * __cdecl WebCore::findValue(char const *,unsigned int)" (?findValue@WebCore@@YAPBUValue@1@PBDI@Z)
1>WebCore.lib(CSSParser.obj) : error LNK2001: �޷��������ⲿ���� "int __cdecl cssyyparse(void *)" (?cssyyparse@@YAHPAX@Z)
1>WebCore.lib(ResourceHandleManager.obj) : error LNK2001: �޷��������ⲿ���� __imp__curl_version_info
1>WebCore.lib(XPathParser.obj) : error LNK2001: �޷��������ⲿ���� "int __cdecl xpathyyparse(void *)" (?xpathyyparse@@YAHPAX@Z)