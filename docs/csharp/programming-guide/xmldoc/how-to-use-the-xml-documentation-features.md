---
title: Jak korzystać z funkcji dokumentacji XML — C# Przewodnik programowania
ms.date: 06/01/2018
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: 5de94b1f1ab44f954b5bab9f8b5212c33325c19d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75696717"
---
# <a name="how-to-use-the-xml-documentation-features"></a>Używanie funkcji dokumentacji XML

Poniższy przykład zawiera podstawowe Omówienie typu, który został udokumentowany.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

Przykład generuje plik. XML o następującej zawartości:

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

To polecenie tworzy plik XML *xmlsample. XML*, który można wyświetlić w przeglądarce lub za pomocą polecenia Type.

## <a name="robust-programming"></a>Niezawodne programowanie

Dokumentacja XML zaczyna się od///. Podczas tworzenia nowego projektu kreatory umieszczają w nim kilka początkowych///wierszy. Przetwarzanie tych komentarzy ma pewne ograniczenia:

- Dokumentacja musi być poprawnie sformułowanym plikiem XML. Jeśli kod XML nie jest poprawnie sformułowany, generowane jest ostrzeżenie, a plik dokumentacji będzie zawierać komentarz informujący o wystąpieniu błędu.

- Deweloperzy mogą bezpłatnie tworzyć własne zestawy tagów. Istnieje zalecany zestaw tagów (zobacz [zalecane Tagi dla komentarzy do dokumentacji](recommended-tags-for-documentation-comments.md)). Niektóre z zalecanych tagów mają specjalne znaczenie:

  - Tag \<param > służy do opisywania parametrów. Jeśli jest używany, kompilator sprawdza, czy parametr istnieje i że wszystkie parametry zostały opisane w dokumentacji. Jeśli weryfikacja nie powiodła się, kompilator generuje ostrzeżenie.

  - Atrybut `cref` może być dołączany do dowolnego tagu w celu udostępnienia odwołania do elementu kodu. Kompilator sprawdza, czy ten element kodu istnieje. Jeśli weryfikacja nie powiodła się, kompilator generuje ostrzeżenie. Kompilator przestrzega wszelkich instrukcji `using`, gdy szuka typu opisanego w atrybucie `cref`.

  - Tag \<Summary > jest używany przez funkcję IntelliSense w programie Visual Studio do wyświetlania dodatkowych informacji na temat typu lub elementu członkowskiego.

    > [!NOTE]
    > Plik XML nie zawiera pełnych informacji o typie i elementach członkowskich (na przykład nie zawierają żadnych informacji o typie). Aby uzyskać pełne informacje na temat typu lub elementu członkowskiego, należy użyć pliku dokumentacji wraz z odbiciem w rzeczywistym typie lub elemencie członkowskim.

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [-doc (C# opcje kompilatora)](../../language-reference/compiler-options/doc-compiler-option.md)
- [Komentarze dokumentacji XML](./index.md)
- [Procesor dokumentacji DocFX](https://dotnet.github.io/docfx/)
- [Procesor dokumentacji Sandcastle](https://github.com/EWSoftware/SHFB)
