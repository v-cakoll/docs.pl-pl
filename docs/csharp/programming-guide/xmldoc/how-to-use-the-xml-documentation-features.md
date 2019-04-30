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
# <a name="how-to-use-the-xml-documentation-features"></a>Instrukcje: Użycie funkcji dokumentacji XML

Poniższy przykład zawiera omówienie podstawowych typów, które zostały opisane.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

Przykład generuje plik XML z następującą zawartością:

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

Aby skompilować przykład, wpisz następujące polecenie w wierszu:

`csc XMLsample.cs /doc:XMLsample.xml`

To polecenie tworzy plik XML *XMLsample.xml*, które można wyświetlić w przeglądarce lub przy użyciu polecenia typu.

## <a name="robust-programming"></a>Skuteczne programowanie

Dokumentacja XML rozpoczyna się od / / /. Podczas tworzenia nowego projektu kreatorów umieścić niektóre modułu uruchamiającego / / / linie w dla Ciebie. Przetwarzanie te komentarze mają pewne ograniczenia:

- Dokumentacja musi być poprawnie sformułowany XML. Jeśli plik XML nie jest poprawnie sformułowany, generowane jest ostrzeżenie, a plik dokumentacja będzie zawierać komentarz, który mówi, że wystąpił błąd podczas.

- Deweloperzy są bezpłatne tworzenie własnych zestawów tagów. Jest zalecany zestaw znaczników (patrz [zalecane tagi przeznaczone do komentarzy dokumentacji](recommended-tags-for-documentation-comments.md)). Niektóre zalecane tagi mają specjalne znaczenie:

  - \<Param > tag jest używany do opisania parametrów. Jeśli używany, kompilator sprawdza, czy parametr istnieje i czy wszystkie parametry są opisane w dokumentacji. Jeśli weryfikacja nie powiodła się, kompilator generuje ostrzeżenie.

  - `cref` Atrybutu mogą być dołączane do każdego znacznika, aby zapewnić odwołanie do elementu kodu. Kompilator sprawdza, czy ten element kodu istnieje. Jeśli weryfikacja nie powiodła się, kompilator generuje ostrzeżenie. Kompilator stosuje się do dowolnej `using` instrukcji będzie szukał typu z opisem w temacie `cref` atrybutu.

  - \<Podsumowania > tag jest używany przez funkcję IntelliSense w programie Visual Studio, aby wyświetlić dodatkowe informacje na temat typu lub elementu członkowskiego.

    > [!NOTE]
    > Plik XML nie zawiera pełne informacje na temat typów i elementów członkowskich (na przykład, go nie zawiera żadnych informacji o typie). Aby uzyskać pełne informacje dotyczące typu lub elementu członkowskiego, należy użyć pliku dokumentacji wraz z odbicia na rzeczywisty typ lub element członkowski.

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [/ doc (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)
- [Komentarze dokumentacji XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
