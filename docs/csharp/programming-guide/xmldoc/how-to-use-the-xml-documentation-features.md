---
title: 'Instrukcje: Korzystanie z funkcji dokumentacji XML — C# Przewodnik programowania'
ms.custom: seodec18
ms.date: 06/01/2018
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: 259f0d5e7e1a67a273bccc7847c38a4d694c69ba
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588108"
---
# <a name="how-to-use-the-xml-documentation-features"></a><span data-ttu-id="c6775-102">Instrukcje: Korzystanie z funkcji dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="c6775-102">How to: Use the XML documentation features</span></span>

<span data-ttu-id="c6775-103">Poniższy przykład zawiera podstawowe Omówienie typu, który został udokumentowany.</span><span class="sxs-lookup"><span data-stu-id="c6775-103">The following sample provides a basic overview of a type that has been documented.</span></span>

## <a name="example"></a><span data-ttu-id="c6775-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c6775-104">Example</span></span>

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

<span data-ttu-id="c6775-105">Przykład generuje plik. XML o następującej zawartości:</span><span class="sxs-lookup"><span data-stu-id="c6775-105">The example generates an .xml file with the following contents:</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="c6775-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c6775-106">Compiling the code</span></span>

<span data-ttu-id="c6775-107">Aby skompilować przykład, wpisz następujący wiersz polecenia:</span><span class="sxs-lookup"><span data-stu-id="c6775-107">To compile the example, type the following command line:</span></span>

`csc XMLsample.cs /doc:XMLsample.xml`

<span data-ttu-id="c6775-108">To polecenie tworzy plik XML *xmlsample. XML*, który można wyświetlić w przeglądarce lub za pomocą polecenia Type.</span><span class="sxs-lookup"><span data-stu-id="c6775-108">This command creates the XML file *XMLsample.xml*, which you can view in your browser or by using the TYPE command.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="c6775-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="c6775-109">Robust programming</span></span>

<span data-ttu-id="c6775-110">Dokumentacja XML zaczyna się od///.</span><span class="sxs-lookup"><span data-stu-id="c6775-110">XML documentation starts with ///.</span></span> <span data-ttu-id="c6775-111">Podczas tworzenia nowego projektu kreatory umieszczają w nim kilka początkowych///wierszy.</span><span class="sxs-lookup"><span data-stu-id="c6775-111">When you create a new project, the wizards put some starter /// lines in for you.</span></span> <span data-ttu-id="c6775-112">Przetwarzanie tych komentarzy ma pewne ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="c6775-112">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="c6775-113">Dokumentacja musi być poprawnie sformułowanym plikiem XML.</span><span class="sxs-lookup"><span data-stu-id="c6775-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="c6775-114">Jeśli kod XML nie jest poprawnie sformułowany, generowane jest ostrzeżenie, a plik dokumentacji będzie zawierać komentarz informujący o wystąpieniu błędu.</span><span class="sxs-lookup"><span data-stu-id="c6775-114">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>

- <span data-ttu-id="c6775-115">Deweloperzy mogą bezpłatnie tworzyć własne zestawy tagów.</span><span class="sxs-lookup"><span data-stu-id="c6775-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="c6775-116">Istnieje zalecany zestaw tagów (zobacz [zalecane Tagi dla komentarzy do dokumentacji](recommended-tags-for-documentation-comments.md)).</span><span class="sxs-lookup"><span data-stu-id="c6775-116">There is a recommended set of tags (see [Recommended tags for documentation comments](recommended-tags-for-documentation-comments.md)).</span></span> <span data-ttu-id="c6775-117">Niektóre z zalecanych tagów mają specjalne znaczenie:</span><span class="sxs-lookup"><span data-stu-id="c6775-117">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="c6775-118">Tag \<> param służy do opisywania parametrów.</span><span class="sxs-lookup"><span data-stu-id="c6775-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="c6775-119">Jeśli jest używany, kompilator sprawdza, czy parametr istnieje i że wszystkie parametry zostały opisane w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="c6775-119">If used, the compiler verifies that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="c6775-120">Jeśli weryfikacja nie powiodła się, kompilator generuje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="c6775-120">If the verification failed, the compiler issues a warning.</span></span>

  - <span data-ttu-id="c6775-121">Ten `cref` atrybut może być dołączany do dowolnego tagu w celu zapewnienia odwołania do elementu kodu.</span><span class="sxs-lookup"><span data-stu-id="c6775-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="c6775-122">Kompilator sprawdza, czy ten element kodu istnieje.</span><span class="sxs-lookup"><span data-stu-id="c6775-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="c6775-123">Jeśli weryfikacja nie powiodła się, kompilator generuje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="c6775-123">If the verification failed, the compiler issues a warning.</span></span> <span data-ttu-id="c6775-124">Kompilator przestrzega wszelkich `using` instrukcji, gdy szuka typu opisanego `cref` w atrybucie.</span><span class="sxs-lookup"><span data-stu-id="c6775-124">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="c6775-125">Tag \<> podsumowujący jest używany przez funkcję IntelliSense w programie Visual Studio do wyświetlania dodatkowych informacji na temat typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="c6775-125">The \<summary> tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c6775-126">Plik XML nie zawiera pełnych informacji o typie i elementach członkowskich (na przykład nie zawierają żadnych informacji o typie).</span><span class="sxs-lookup"><span data-stu-id="c6775-126">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="c6775-127">Aby uzyskać pełne informacje na temat typu lub elementu członkowskiego, należy użyć pliku dokumentacji wraz z odbiciem w rzeczywistym typie lub elemencie członkowskim.</span><span class="sxs-lookup"><span data-stu-id="c6775-127">To get full information about a type or member, the documentation file must be used together with reflection on the actual type or member.</span></span>

## <a name="see-also"></a><span data-ttu-id="c6775-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c6775-128">See also</span></span>

- [<span data-ttu-id="c6775-129">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c6775-129">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c6775-130">/doc (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="c6775-130">/doc (C# Compiler Options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="c6775-131">Komentarze dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="c6775-131">XML Documentation Comments</span></span>](./index.md)
