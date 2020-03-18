---
title: Jak korzystać z funkcji dokumentacji XML - Przewodnik programowania C#
ms.date: 06/01/2018
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: e279b13d9216120e25f454faa14dc71ad24c74ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157003"
---
# <a name="how-to-use-the-xml-documentation-features"></a>Używanie funkcji dokumentacji XML

Poniższy przykład zawiera podstawowy przegląd typu, który został udokumentowany.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

Przykład generuje plik *xml* o następującej zawartości.

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

## <a name="compiling-the-code"></a>Kompilowanie kodu

Aby skompilować przykład, wpisz następujący wiersz polecenia:

`csc XMLsample.cs /doc:XMLsample.xml`

To polecenie tworzy plik XML *XMLsample.xml*, który można wyświetlić w przeglądarce lub za pomocą polecenia TYPE.

## <a name="robust-programming"></a>Solidne programowanie

Dokumentacja XML zaczyna się od ///. Podczas tworzenia nowego projektu kreatorzy umieszczają dla Ciebie kilka wierszy początkowych ///. Przetwarzanie tych komentarzy ma pewne ograniczenia:

- Dokumentacja musi być dobrze sformułowana XML. Jeśli kod XML nie jest poprawnie sformułowany, generowane jest ostrzeżenie, a plik dokumentacji będzie zawierał komentarz z komunikatem, że wystąpił błąd.

- Deweloperzy mogą tworzyć własny zestaw tagów. Istnieje [zalecany zestaw tagów](recommended-tags-for-documentation-comments.md). Niektóre z zalecanych tagów mają specjalne znaczenie:

  - Znacznik \<> param jest używany do opisywania parametrów. Jeśli jest używany, kompilator sprawdza, czy parametr istnieje i czy wszystkie parametry są opisane w dokumentacji. Jeśli weryfikacja nie powiodła się, kompilator generuje ostrzeżenie.

  - Atrybut `cref` można dołączyć do dowolnego tagu, aby zapewnić odwołanie do elementu kodu. Kompilator sprawdza, czy istnieje ten element kodu. Jeśli weryfikacja nie powiodła się, kompilator generuje ostrzeżenie. Kompilator szanuje `using` wszystkie instrukcje, gdy szuka `cref` typu opisanego w atrybucie.

  - Podsumowanie \<> tag jest używany przez IntelliSense wewnątrz programu Visual Studio do wyświetlania dodatkowych informacji o typie lub e-element.

    > [!NOTE]
    > Plik XML nie zawiera pełnych informacji o typie i członkach (na przykład nie zawiera żadnych informacji o typie). Aby uzyskać pełne informacje o typie lub e-elementosty, plik dokumentacji musi być używany wraz z refleksją na temat rzeczywistego typu lub elementu członkowskiego.

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [-doc (opcje kompilatora C#)](../../language-reference/compiler-options/doc-compiler-option.md)
- [Komentarze dokumentacji XML](./index.md)
- [Procesor dokumentacji DocFX](https://dotnet.github.io/docfx/)
- [Procesor dokumentacji Sandcastle](https://github.com/EWSoftware/SHFB)
