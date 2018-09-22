---
title: '&lt;obejmują&gt; (C# Programming Guide)'
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: 854c8b61fa8164bccfc9451f2f163dab4a56388f
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46568731"
---
# <a name="ltincludegt-c-programming-guide"></a><span data-ttu-id="886c2-102">&lt;obejmują&gt; (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="886c2-102">&lt;include&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="886c2-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="886c2-103">Syntax</span></span>  
  
```xml  
<include file='filename' path='tagpath[@name="id"]' />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="886c2-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="886c2-104">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="886c2-105">Nazwa pliku XML zawierającego dokumentację.</span><span class="sxs-lookup"><span data-stu-id="886c2-105">The name of the XML file containing the documentation.</span></span> <span data-ttu-id="886c2-106">Nazwa pliku może być kwalifikowana ze ścieżką względną do pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="886c2-106">The file name can be qualified with a path relative to the source code file.</span></span> <span data-ttu-id="886c2-107">Ujmij `filename` w znaki pojedynczego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="886c2-107">Enclose `filename` in single quotation marks (' ').</span></span>  
  
 `tagpath`  
 <span data-ttu-id="886c2-108">Ścieżka znaczniki `filename` prowadzi to do tagu `name`.</span><span class="sxs-lookup"><span data-stu-id="886c2-108">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="886c2-109">Zamknij ścieżkę w znaki pojedynczego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="886c2-109">Enclose the path in single quotation marks (' ').</span></span>  
  
 `name`  
 <span data-ttu-id="886c2-110">Określenie nazwy w tagu, który poprzedza komentarzy; `name` będzie miał `id`.</span><span class="sxs-lookup"><span data-stu-id="886c2-110">The name specifier in the tag that precedes the comments; `name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="886c2-111">Identyfikator tagu, który poprzedza komentarze.</span><span class="sxs-lookup"><span data-stu-id="886c2-111">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="886c2-112">Umieść identyfikator w podwójnym cudzysłowie ("").</span><span class="sxs-lookup"><span data-stu-id="886c2-112">Enclose the ID in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="886c2-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="886c2-113">Remarks</span></span>  
 <span data-ttu-id="886c2-114">\<Obejmują > tag pozwala odwoływać się do komentarzy w innym pliku, które opisują typy i elementy członkowskie w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="886c2-114">The \<include> tag lets you refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="886c2-115">Jest to alternatywa do wprowadzania komentarzy dokumentacji bezpośrednio w pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="886c2-115">This is an alternative to placing documentation comments directly in your source code file.</span></span> <span data-ttu-id="886c2-116">Poprzez umieszczenie dokumentacji w oddzielnym pliku, można zastosować kontroli źródła z dokumentacją oddzielnie z kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="886c2-116">By putting the documentation in a separate file, you can apply source control to the documentation separately from the source code.</span></span> <span data-ttu-id="886c2-117">Jedna osoba może mieć wyewidencjonować pliku źródła kodu, a ktoś inny może mieć plik dokumentacji wyewidencjonowany.</span><span class="sxs-lookup"><span data-stu-id="886c2-117">One person can have the source code file checked out and someone else can have the documentation file checked out.</span></span>  
  
 <span data-ttu-id="886c2-118">\<Obejmują > tag używa składni XML XPath.</span><span class="sxs-lookup"><span data-stu-id="886c2-118">The \<include> tag uses the XML XPath syntax.</span></span> <span data-ttu-id="886c2-119">Zajrzyj do dokumentacji wyrażenie XPath sposoby dostosowywania swoje \<obejmują > Użyj.</span><span class="sxs-lookup"><span data-stu-id="886c2-119">Refer to XPath documentation for ways to customize your \<include> use.</span></span>  
  
## <a name="example"></a><span data-ttu-id="886c2-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="886c2-120">Example</span></span>  
 <span data-ttu-id="886c2-121">To jest przykład wieloplikowego.</span><span class="sxs-lookup"><span data-stu-id="886c2-121">This is a multifile example.</span></span> <span data-ttu-id="886c2-122">Pierwszy plik, który używa \<obejmują >, znajduje się poniżej:</span><span class="sxs-lookup"><span data-stu-id="886c2-122">The first file, which uses \<include>, is listed below:</span></span>  
  
 [!code-csharp[csProgGuideDocComments#5](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/include_1.cs)]  
  
 <span data-ttu-id="886c2-123">Drugi plik, xml_include_tag.doc, zawiera następujące komentarzy dokumentacji:</span><span class="sxs-lookup"><span data-stu-id="886c2-123">The second file, xml_include_tag.doc, contains the following documentation comments:</span></span>  
  
```xml  
<MyDocs>  
  
<MyMembers name="test">  
<summary>  
The summary for this type.  
</summary>  
</MyMembers>  
  
<MyMembers name="test2">  
<summary>  
The summary for this other type.  
</summary>  
</MyMembers>  
  
</MyDocs>  
```  
  
## <a name="program-output"></a><span data-ttu-id="886c2-124">Dane wyjściowe programu</span><span class="sxs-lookup"><span data-stu-id="886c2-124">Program Output</span></span>  
 <span data-ttu-id="886c2-125">Następujących danych wyjściowych jest generowany, gdy kompilujesz z klas testowych i Test2 za pomocą następującego polecenia: `/doc:DocFileName.xml.` w programie Visual Studio, określasz opcję Komentarze dokumentacji XML w okienku kompilacji w Projektancie projektu.</span><span class="sxs-lookup"><span data-stu-id="886c2-125">The following output is generated when you compile the Test and Test2 classes with the following command line: `/doc:DocFileName.xml.` In Visual Studio, you specify the XML doc comments option in the Build pane of the Project Designer.</span></span> <span data-ttu-id="886c2-126">Gdy kompilator języka C# widzi \<obejmują > tag, przeszukiwane są przeznaczone do komentarzy dokumentacji w xml_include_tag.doc zamiast bieżącego pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="886c2-126">When the C# compiler sees the \<include> tag, it will search for documentation comments in xml_include_tag.doc instead of the current source file.</span></span> <span data-ttu-id="886c2-127">Kompilator generuje następnie DocFileName.xml i to jest plik, który jest używany przez narzędzia, dokumentację, takich jak [Sandcastle](https://github.com/EWSoftware/SHFB) do produkcji dokumentację.</span><span class="sxs-lookup"><span data-stu-id="886c2-127">The compiler then generates DocFileName.xml, and this is the file that is consumed by documentation tools such as [Sandcastle](https://github.com/EWSoftware/SHFB) to produce the final documentation.</span></span>  
  
```xml  
<?xml version="1.0"?>   
<doc>   
    <assembly>   
        <name>xml_include_tag</name>   
    </assembly>   
    <members>   
        <member name="T:Test">   
            <summary>   
The summary for this type.   
</summary>   
        </member>   
        <member name="T:Test2">   
            <summary>   
The summary for this other type.   
</summary>   
        </member>   
    </members>   
</doc>   
```  
  
## <a name="see-also"></a><span data-ttu-id="886c2-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="886c2-128">See Also</span></span>

- [<span data-ttu-id="886c2-129">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="886c2-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="886c2-130">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="886c2-130">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
