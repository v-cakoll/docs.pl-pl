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
# <a name="how-to-use-the-xml-documentation-features"></a>Porady: użycie funkcji dokumentacji XML

Poniższy przykład zawiera ogólne omówienie typu, który został udokumentowany.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

Przykład generuje plik XML z następującą zawartość:

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

Aby skompilować w przykładzie, wpisz następujące polecenie w wierszu:

`csc XMLsample.cs /doc:XMLsample.xml`

To polecenie tworzy plik XML *XMLsample.xml*, które można wyświetlić w przeglądarce lub za pomocą polecenia typu.

## <a name="robust-programming"></a>Skuteczne programowanie

Plik dokumentacji XML rozpoczyna się od lokalizacje. Podczas tworzenia nowego projektu kreatorów umieść starter lokalizacje wiersze w automatycznie. Przetwarzanie komentarze ma pewne ograniczenia:

- Dokumentację musi być poprawnie sformułowanym XML. Jeśli plik XML nie jest poprawnie sformułowany, generowania ostrzeżeń i pliku dokumentacji będzie zawierać komentarz z informacją, że wystąpił błąd podczas.

- Deweloperzy mogą tworzyć własne zestawu tagów. Jest zalecany zestaw tagi (zobacz [zalecane tagi przeznaczone do komentarzy dokumentacji](recommended-tags-for-documentation-comments.md)). Niektóre zalecane znaczniki mają specjalne znaczenie:

  - \<Param > tag jest używany do opisywania parametrów. Jeśli używana, kompilator sprawdza, czy parametr istnieje i że wszystkie parametry są opisane w dokumentacji. Jeśli weryfikacja nie powiodła się, kompilator generuje ostrzeżenie.

  - `cref` Atrybut może zostać dołączony do żadnych znacznik w celu zapewnienia odwołania do elementu kodu. Kompilator sprawdza, czy istnieje tego elementu kodu. Jeśli weryfikacja nie powiodła się, kompilator generuje ostrzeżenie. Kompilator szanuje żadnego `using` instrukcje podczas wyszukiwania typu opisanego w `cref` atrybutu.

  - \<Podsumowania > tag jest używany przez funkcję IntelliSense w programie Visual Studio, aby wyświetlić dodatkowe informacje na temat typu lub elementu członkowskiego.

    > [!NOTE]
    > Plik XML nie zapewnia pełne informacje dotyczące typu i elementów członkowskich (na przykład go nie zawiera żadnych informacji o typie). Aby uzyskać pełne informacje dotyczące typu lub elementu członkowskiego, plik dokumentacji musi być używany razem odbicia na rzeczywisty typ lub element członkowski.

## <a name="see-also"></a>Zobacz także

[Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
[/ doc (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
[Komentarze dokumentacji XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
