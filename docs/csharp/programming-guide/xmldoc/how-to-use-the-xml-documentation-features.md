---
title: 'Porady: użycie funkcji dokumentacji XML (C# przewodnik programowania w języku)'
ms.date: 06/01/2018
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: b82f92cc034a13e8867cfb56866200101ab77b9b
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728735"
---
# <a name="how-to-use-the-xml-documentation-features"></a><span data-ttu-id="465ab-102">Porady: użycie funkcji dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="465ab-102">How to: Use the XML documentation features</span></span>

<span data-ttu-id="465ab-103">Poniższy przykład zawiera ogólne omówienie typu, który został udokumentowany.</span><span class="sxs-lookup"><span data-stu-id="465ab-103">The following sample provides a basic overview of a type that has been documented.</span></span>

## <a name="example"></a><span data-ttu-id="465ab-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="465ab-104">Example</span></span>

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

<span data-ttu-id="465ab-105">Przykład generuje plik XML z następującą zawartość:</span><span class="sxs-lookup"><span data-stu-id="465ab-105">The example generates an .xml file with the following contents:</span></span>

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>xmlsample</name>
    </assembly>
    <members>
        <member name="T:TestClass">
            <summary>
            Class level summary documentation goes here.
            </summary>
            <remarks>
            Longer comments can be associated with a type or member through
            the remarks tag.
            </remarks>
        </member>
        <member name="F:TestClass._name">
            <summary>
            Store for the Name property.
            </summary>
        </member>
        <member name="M:TestClass.#ctor">
            <summary>
            The class constructor.
            </summary>
        </member>
        <member name="P:TestClass.Name">
            <summary>
            Name property.
            </summary>
            <value>
            A value tag is used to describe the property value.
            </value>
        </member>
        <member name="M:TestClass.SomeMethod(System.String)">
            <summary>
            Description for SomeMethod.
            </summary>
            <param name="s"> Parameter description for s goes here.</param>
            <seealso cref="T:System.String">
            You can use the cref attribute on any tag to reference a type or member 
            and the compiler will check that the reference exists.
            </seealso>
        </member>
        <member name="M:TestClass.SomeOtherMethod">
            <summary>
            Some other method.
            </summary>
            <returns>
            Return values are described through the returns tag.
            </returns>
            <seealso cref="M:TestClass.SomeMethod(System.String)">
            Notice the use of the cref attribute to reference a specific method.
            </seealso>
        </member>
        <member name="M:TestClass.Main(System.String[])">
            <summary>
            The entry point for the application.
            </summary>
            <param name="args"> A list of command line arguments.</param>
        </member>
        <member name="T:TestInterface">
            <summary>
            Documentation that describes the interface goes here.
            </summary>
            <remarks>
            Details about the interface go here.
            </remarks>
        </member>
        <member name="M:TestInterface.InterfaceMethod(System.Int32)">
            <summary>
            Documentation that describes the method goes here.
            </summary>
            <param name="n">
            Parameter n requires an integer argument.
            </param>
            <returns>
            The method returns an integer.
            </returns>
        </member>
    </members>
</doc>
```

## <a name="compiling-the-code"></a><span data-ttu-id="465ab-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="465ab-106">Compiling the code</span></span>

<span data-ttu-id="465ab-107">Aby skompilować w przykładzie, wpisz następujące polecenie w wierszu:</span><span class="sxs-lookup"><span data-stu-id="465ab-107">To compile the example, type the following command line:</span></span>

`csc XMLsample.cs /doc:XMLsample.xml`

<span data-ttu-id="465ab-108">To polecenie tworzy plik XML *XMLsample.xml*, które można wyświetlić w przeglądarce lub za pomocą polecenia typu.</span><span class="sxs-lookup"><span data-stu-id="465ab-108">This command creates the XML file *XMLsample.xml*, which you can view in your browser or by using the TYPE command.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="465ab-109">Skuteczne programowanie</span><span class="sxs-lookup"><span data-stu-id="465ab-109">Robust programming</span></span>

<span data-ttu-id="465ab-110">Plik dokumentacji XML rozpoczyna się od lokalizacje.</span><span class="sxs-lookup"><span data-stu-id="465ab-110">XML documentation starts with ///.</span></span> <span data-ttu-id="465ab-111">Podczas tworzenia nowego projektu kreatorów umieść starter lokalizacje wiersze w automatycznie.</span><span class="sxs-lookup"><span data-stu-id="465ab-111">When you create a new project, the wizards put some starter /// lines in for you.</span></span> <span data-ttu-id="465ab-112">Przetwarzanie komentarze ma pewne ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="465ab-112">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="465ab-113">Dokumentację musi być poprawnie sformułowanym XML.</span><span class="sxs-lookup"><span data-stu-id="465ab-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="465ab-114">Jeśli plik XML nie jest poprawnie sformułowany, generowania ostrzeżeń i pliku dokumentacji będzie zawierać komentarz z informacją, że wystąpił błąd podczas.</span><span class="sxs-lookup"><span data-stu-id="465ab-114">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>

- <span data-ttu-id="465ab-115">Deweloperzy mogą tworzyć własne zestawu tagów.</span><span class="sxs-lookup"><span data-stu-id="465ab-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="465ab-116">Jest zalecany zestaw tagi (zobacz [zalecane tagi przeznaczone do komentarzy dokumentacji](recommended-tags-for-documentation-comments.md)).</span><span class="sxs-lookup"><span data-stu-id="465ab-116">There is a recommended set of tags (see [Recommended tags for documentation comments](recommended-tags-for-documentation-comments.md)).</span></span> <span data-ttu-id="465ab-117">Niektóre zalecane znaczniki mają specjalne znaczenie:</span><span class="sxs-lookup"><span data-stu-id="465ab-117">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="465ab-118">\<Param > tag jest używany do opisywania parametrów.</span><span class="sxs-lookup"><span data-stu-id="465ab-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="465ab-119">Jeśli używana, kompilator sprawdza, czy parametr istnieje i że wszystkie parametry są opisane w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="465ab-119">If used, the compiler verifies that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="465ab-120">Jeśli weryfikacja nie powiodła się, kompilator generuje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="465ab-120">If the verification failed, the compiler issues a warning.</span></span>

  - <span data-ttu-id="465ab-121">`cref` Atrybut może zostać dołączony do żadnych znacznik w celu zapewnienia odwołania do elementu kodu.</span><span class="sxs-lookup"><span data-stu-id="465ab-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="465ab-122">Kompilator sprawdza, czy istnieje tego elementu kodu.</span><span class="sxs-lookup"><span data-stu-id="465ab-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="465ab-123">Jeśli weryfikacja nie powiodła się, kompilator generuje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="465ab-123">If the verification failed, the compiler issues a warning.</span></span> <span data-ttu-id="465ab-124">Kompilator szanuje żadnego `using` instrukcje podczas wyszukiwania typu opisanego w `cref` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="465ab-124">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="465ab-125">\<Podsumowania > tag jest używany przez funkcję IntelliSense w programie Visual Studio, aby wyświetlić dodatkowe informacje na temat typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="465ab-125">The \<summary> tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>

    > [!NOTE]
    > <span data-ttu-id="465ab-126">Plik XML nie zapewnia pełne informacje dotyczące typu i elementów członkowskich (na przykład go nie zawiera żadnych informacji o typie).</span><span class="sxs-lookup"><span data-stu-id="465ab-126">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="465ab-127">Aby uzyskać pełne informacje dotyczące typu lub elementu członkowskiego, plik dokumentacji musi być używany razem odbicia na rzeczywisty typ lub element członkowski.</span><span class="sxs-lookup"><span data-stu-id="465ab-127">To get full information about a type or member, the documentation file must be used together with reflection on the actual type or member.</span></span>

## <a name="see-also"></a><span data-ttu-id="465ab-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="465ab-128">See also</span></span>

[<span data-ttu-id="465ab-129">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="465ab-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="465ab-130">/ doc (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="465ab-130">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
[<span data-ttu-id="465ab-131">Komentarze dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="465ab-131">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
