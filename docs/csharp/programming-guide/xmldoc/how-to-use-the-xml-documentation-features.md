---
title: 'Porady: użycie funkcji dokumentacji XML (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: d7f1f51040033cf25f7f1aefb04d249e6e028ca3
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2018
---
# <a name="how-to-use-the-xml-documentation-features-c-programming-guide"></a><span data-ttu-id="78f7b-102">Porady: użycie funkcji dokumentacji XML (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="78f7b-102">How to: Use the XML Documentation Features (C# Programming Guide)</span></span>
<span data-ttu-id="78f7b-103">Poniższy przykład zawiera ogólne omówienie typu, który został udokumentowany.</span><span class="sxs-lookup"><span data-stu-id="78f7b-103">The following sample provides a basic overview of a type that has been documented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78f7b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="78f7b-104">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]  

<span data-ttu-id="78f7b-105">Przykład generuje plik XML z następującą zawartość:</span><span class="sxs-lookup"><span data-stu-id="78f7b-105">The example generates an .xml file with the following contents:</span></span>

```xml  
<?xml version="1.0"?>  
<doc>  
 <assembly>  
 <name>xmlsample</name>  
 </assembly>  
 <members>  
 <member name="T:SomeClass">  
 <summary>  
 Class level summary documentation goes here.</summary>  
 <remarks>  
 Longer comments can be associated with a type or member  
 through the remarks tag</remarks>  
 </member>  
 <member name="F:SomeClass.m_Name">  
 <summary>  
 Store for the name property</summary>  
 </member>  
 <member name="M:SomeClass.#ctor">  
 <summary>The class constructor.</summary>  
 </member>  
 <member name="M:SomeClass.SomeMethod(System.String)">  
 <summary>  
 Description for SomeMethod.</summary>  
 <param name="s"> Parameter description for s goes here</param>  
 <seealso cref="T:System.String">  
 You can use the cref attribute on any tag to reference a type or member  
 and the compiler will check that the reference exists. </seealso>  
 </member>  
 <member name="M:SomeClass.SomeOtherMethod">  
 <summary>  
 Some other method. </summary>  
 <returns>  
 Return results are described through the returns tag.</returns>  
 <seealso cref="M:SomeClass.SomeMethod(System.String)">  
 Notice the use of the cref attribute to reference a specific method </seealso>  
 </member>  
 <member name="M:SomeClass.Main(System.String[])">  
 <summary>  
 The entry point for the application.  
 </summary>  
 <param name="args"> A list of command line arguments</param>  
 </member>  
 <member name="P:SomeClass.Name">  
 <summary>  
 Name property </summary>  
 <value>A value tag is used to describe the property value</value>  
 </member>  
 </members>  
</doc>   
```

## <a name="compiling-the-code"></a><span data-ttu-id="78f7b-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="78f7b-106">Compiling the Code</span></span>  
 <span data-ttu-id="78f7b-107">Aby skompilować w przykładzie, wpisz następujące polecenie w wierszu:</span><span class="sxs-lookup"><span data-stu-id="78f7b-107">To compile the example, type the following command line:</span></span>  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 <span data-ttu-id="78f7b-108">Spowoduje to utworzenie pliku XML XMLsample.xml, które można wyświetlić w przeglądarce lub za pomocą polecenia typu.</span><span class="sxs-lookup"><span data-stu-id="78f7b-108">This will create the XML file XMLsample.xml, which you can view in your browser or by using the TYPE command.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="78f7b-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="78f7b-109">Robust Programming</span></span>  
 <span data-ttu-id="78f7b-110">Plik dokumentacji XML rozpoczyna się od lokalizacje.</span><span class="sxs-lookup"><span data-stu-id="78f7b-110">XML documentation starts with ///.</span></span> <span data-ttu-id="78f7b-111">Podczas tworzenia nowego projektu kreatorów umieść starter lokalizacje wiersze w automatycznie.</span><span class="sxs-lookup"><span data-stu-id="78f7b-111">When you create a new project, the wizards put some starter /// lines in for you.</span></span> <span data-ttu-id="78f7b-112">Przetwarzanie komentarze ma pewne ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="78f7b-112">The processing of these comments has some restrictions:</span></span>  
  
-   <span data-ttu-id="78f7b-113">Dokumentację musi być poprawnie sformułowanym XML.</span><span class="sxs-lookup"><span data-stu-id="78f7b-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="78f7b-114">Jeśli plik XML nie jest poprawnie sformułowany, generowania ostrzeżeń i pliku dokumentacji będzie zawierać komentarz z informacją, że wystąpił błąd podczas.</span><span class="sxs-lookup"><span data-stu-id="78f7b-114">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>  
  
-   <span data-ttu-id="78f7b-115">Deweloperzy mogą tworzyć własne zestawu tagów.</span><span class="sxs-lookup"><span data-stu-id="78f7b-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="78f7b-116">Jest zalecany zestaw tagi (zobacz [zalecane tagi przeznaczone do komentarzy dokumentacji](recommended-tags-for-documentation-comments.md)).</span><span class="sxs-lookup"><span data-stu-id="78f7b-116">There is a recommended set of tags (see [Recommended tags for documentation comments](recommended-tags-for-documentation-comments.md)).</span></span> <span data-ttu-id="78f7b-117">Niektóre zalecane znaczniki mają specjalne znaczenie:</span><span class="sxs-lookup"><span data-stu-id="78f7b-117">Some of the recommended tags have special meanings:</span></span>  
  
    -   <span data-ttu-id="78f7b-118">\<Param > tag jest używany do opisywania parametrów.</span><span class="sxs-lookup"><span data-stu-id="78f7b-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="78f7b-119">Jeśli używana, kompilator sprawdza, czy parametr istnieje i że wszystkie parametry są opisane w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="78f7b-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="78f7b-120">Jeśli weryfikacja nie powiodła się, kompilator generuje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="78f7b-120">If the verification failed, the compiler issues a warning.</span></span>  
  
    -   <span data-ttu-id="78f7b-121">`cref` Atrybut może zostać dołączony do żadnych znacznik w celu zapewnienia odwołania do elementu kodu.</span><span class="sxs-lookup"><span data-stu-id="78f7b-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="78f7b-122">Kompilator będzie Sprawdź, czy istnieje tego elementu kodu.</span><span class="sxs-lookup"><span data-stu-id="78f7b-122">The compiler will verify that this code element exists.</span></span> <span data-ttu-id="78f7b-123">Jeśli weryfikacja nie powiodła się, kompilator generuje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="78f7b-123">If the verification failed, the compiler issues a warning.</span></span> <span data-ttu-id="78f7b-124">Kompilator szanuje żadnego `using` instrukcje podczas wyszukiwania typu opisanego w `cref` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="78f7b-124">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>  
  
    -   <span data-ttu-id="78f7b-125">\<Podsumowania > tag jest używany przez funkcję IntelliSense w programie Visual Studio, aby wyświetlić dodatkowe informacje na temat typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="78f7b-125">The \<summary> tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="78f7b-126">Plik XML nie zapewnia pełne informacje dotyczące typu i elementów członkowskich (na przykład go nie zawiera żadnych informacji o typie).</span><span class="sxs-lookup"><span data-stu-id="78f7b-126">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="78f7b-127">Aby uzyskać pełne informacje dotyczące typu lub elementu członkowskiego, plik dokumentacji musi być używany razem odbicia na rzeczywisty typ lub element członkowski.</span><span class="sxs-lookup"><span data-stu-id="78f7b-127">To get full information about a type or member, the documentation file must be used together with reflection on the actual type or member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78f7b-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="78f7b-128">See Also</span></span>  
 [<span data-ttu-id="78f7b-129">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="78f7b-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="78f7b-130">/ doc (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="78f7b-130">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [<span data-ttu-id="78f7b-131">Komentarze dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="78f7b-131">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
