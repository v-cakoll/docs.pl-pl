---
title: 'Instrukcje: Użycie funkcji dokumentacji XML — C# Programming Guide'
ms.custom: seodec18
ms.date: 06/01/2018
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: 893dc726f7b4ee2d2afa69f63d13d1f11a4692db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61708200"
---
# <a name="how-to-use-the-xml-documentation-features"></a><span data-ttu-id="8ca72-102">Instrukcje: Użycie funkcji dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="8ca72-102">How to: Use the XML documentation features</span></span>

<span data-ttu-id="8ca72-103">Poniższy przykład zawiera omówienie podstawowych typów, które zostały opisane.</span><span class="sxs-lookup"><span data-stu-id="8ca72-103">The following sample provides a basic overview of a type that has been documented.</span></span>

## <a name="example"></a><span data-ttu-id="8ca72-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ca72-104">Example</span></span>

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

<span data-ttu-id="8ca72-105">Przykład generuje plik XML z następującą zawartością:</span><span class="sxs-lookup"><span data-stu-id="8ca72-105">The example generates an .xml file with the following contents:</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="8ca72-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="8ca72-106">Compiling the code</span></span>

<span data-ttu-id="8ca72-107">Aby skompilować przykład, wpisz następujące polecenie w wierszu:</span><span class="sxs-lookup"><span data-stu-id="8ca72-107">To compile the example, type the following command line:</span></span>

`csc XMLsample.cs /doc:XMLsample.xml`

<span data-ttu-id="8ca72-108">To polecenie tworzy plik XML *XMLsample.xml*, które można wyświetlić w przeglądarce lub przy użyciu polecenia typu.</span><span class="sxs-lookup"><span data-stu-id="8ca72-108">This command creates the XML file *XMLsample.xml*, which you can view in your browser or by using the TYPE command.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="8ca72-109">Skuteczne programowanie</span><span class="sxs-lookup"><span data-stu-id="8ca72-109">Robust programming</span></span>

<span data-ttu-id="8ca72-110">Dokumentacja XML rozpoczyna się od / / /.</span><span class="sxs-lookup"><span data-stu-id="8ca72-110">XML documentation starts with ///.</span></span> <span data-ttu-id="8ca72-111">Podczas tworzenia nowego projektu kreatorów umieścić niektóre modułu uruchamiającego / / / linie w dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="8ca72-111">When you create a new project, the wizards put some starter /// lines in for you.</span></span> <span data-ttu-id="8ca72-112">Przetwarzanie te komentarze mają pewne ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="8ca72-112">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="8ca72-113">Dokumentacja musi być poprawnie sformułowany XML.</span><span class="sxs-lookup"><span data-stu-id="8ca72-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="8ca72-114">Jeśli plik XML nie jest poprawnie sformułowany, generowane jest ostrzeżenie, a plik dokumentacja będzie zawierać komentarz, który mówi, że wystąpił błąd podczas.</span><span class="sxs-lookup"><span data-stu-id="8ca72-114">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>

- <span data-ttu-id="8ca72-115">Deweloperzy są bezpłatne tworzenie własnych zestawów tagów.</span><span class="sxs-lookup"><span data-stu-id="8ca72-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="8ca72-116">Jest zalecany zestaw znaczników (patrz [zalecane tagi przeznaczone do komentarzy dokumentacji](recommended-tags-for-documentation-comments.md)).</span><span class="sxs-lookup"><span data-stu-id="8ca72-116">There is a recommended set of tags (see [Recommended tags for documentation comments](recommended-tags-for-documentation-comments.md)).</span></span> <span data-ttu-id="8ca72-117">Niektóre zalecane tagi mają specjalne znaczenie:</span><span class="sxs-lookup"><span data-stu-id="8ca72-117">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="8ca72-118">\<Param > tag jest używany do opisania parametrów.</span><span class="sxs-lookup"><span data-stu-id="8ca72-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="8ca72-119">Jeśli używany, kompilator sprawdza, czy parametr istnieje i czy wszystkie parametry są opisane w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="8ca72-119">If used, the compiler verifies that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="8ca72-120">Jeśli weryfikacja nie powiodła się, kompilator generuje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="8ca72-120">If the verification failed, the compiler issues a warning.</span></span>

  - <span data-ttu-id="8ca72-121">`cref` Atrybutu mogą być dołączane do każdego znacznika, aby zapewnić odwołanie do elementu kodu.</span><span class="sxs-lookup"><span data-stu-id="8ca72-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="8ca72-122">Kompilator sprawdza, czy ten element kodu istnieje.</span><span class="sxs-lookup"><span data-stu-id="8ca72-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="8ca72-123">Jeśli weryfikacja nie powiodła się, kompilator generuje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="8ca72-123">If the verification failed, the compiler issues a warning.</span></span> <span data-ttu-id="8ca72-124">Kompilator stosuje się do dowolnej `using` instrukcji będzie szukał typu z opisem w temacie `cref` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="8ca72-124">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="8ca72-125">\<Podsumowania > tag jest używany przez funkcję IntelliSense w programie Visual Studio, aby wyświetlić dodatkowe informacje na temat typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="8ca72-125">The \<summary> tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8ca72-126">Plik XML nie zawiera pełne informacje na temat typów i elementów członkowskich (na przykład, go nie zawiera żadnych informacji o typie).</span><span class="sxs-lookup"><span data-stu-id="8ca72-126">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="8ca72-127">Aby uzyskać pełne informacje dotyczące typu lub elementu członkowskiego, należy użyć pliku dokumentacji wraz z odbicia na rzeczywisty typ lub element członkowski.</span><span class="sxs-lookup"><span data-stu-id="8ca72-127">To get full information about a type or member, the documentation file must be used together with reflection on the actual type or member.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ca72-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ca72-128">See also</span></span>

- [<span data-ttu-id="8ca72-129">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8ca72-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="8ca72-130">/ doc (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="8ca72-130">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="8ca72-131">Komentarze dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="8ca72-131">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
