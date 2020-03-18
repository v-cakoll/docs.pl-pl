---
title: Ograniczniki dla tagów dokumentacji - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: dd4ddb3b324bd6d235efb541c90875dbe9ed4c2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789832"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a>Ograniczniki dla tagów dokumentacji (przewodnik programowania Języka C#)

Korzystanie z komentarzy doc XML wymaga ograniczników, które wskazują do kompilatora, gdzie komentarz dokumentacji zaczyna się i kończy. Znaczników dokumentacji XML można używać następujących rodzajów ograniczników:

- `///`

  Ogranicznik jednoliniowy. Jest to formularz, który jest wyświetlany w przykładach dokumentacji i używane przez szablony projektu Visual C#. Jeśli po ograniczniku znajduje się znak odstępu, znak ten nie jest uwzględniany w danych wyjściowych XML.

  > [!NOTE]
  > Ide programu Visual Studio ma funkcję o nazwie Inteligentna edycja komentarza, która automatycznie wstawia \<> podsumowania i \</summary> tagów i przenosi kursor w tych tagach po wpisaniu `///` ogranicznika w Edytorze kodu. Tę funkcję można włączyć lub wyłączyć w [oknie dialogowym Opcje](/visualstudio/ide/reference/options-text-editor-csharp-advanced).
  
- `/** */`

  Wieloliniowe ograniczniki.

  Istnieją pewne reguły formatowania, których należy `/** */` przestrzegać podczas korzystania z ograniczników:
  
  - W wierszu zawierającym `/**` ogranicznik, jeśli pozostała część wiersza jest odstępem, wiersz nie jest przetwarzany dla komentarzy. Jeśli pierwszym znakiem `/**` po ograniczniku jest biały znak, ten znak odstępu jest ignorowany, a reszta wiersza jest przetwarzana. W przeciwnym razie cały tekst `/**` wiersza po ogranicznik jest przetwarzany jako część komentarza.

  - W wierszu zawierającym `*/` ogranicznik, jeśli istnieje tylko biały `*/` znak do ogranicznika, wiersz ten jest ignorowany. W przeciwnym razie tekst w `*/` wierszu do ogranicznika jest przetwarzany jako część komentarza, z zastrzeżeniem reguł dopasowywania wzorców opisanych w poniższym punktorze.
  
  - Dla wierszy po tym, `/**` który zaczyna się od ogranicznika, kompilator szuka wspólnego wzorca na początku każdego wiersza. Wzór może składać się z opcjonalnego`*`odstępu i gwiazdki ( ), a następnie bardziej opcjonalnego odstępu. Jeśli kompilator znajdzie wspólny wzorzec na początku `/**` każdego wiersza, `*/` który nie zaczyna się od ogranicznika lub ogranicznika, ignoruje ten wzorzec dla każdego wiersza.

  Poniższe przykłady ilustrują te reguły.

  - Jedyną częścią następującego komentarza, który zostanie przetworzony, `<summary>`jest wiersz, który zaczyna się od . Trzy formaty znaczników generują te same komentarze.

    ```csharp
    /** <summary>text</summary> */

    /**
    <summary>text</summary>
    */

    /**
     * <summary>text</summary>
    */
    ```

  - Kompilator identyfikuje wspólny \* wzorzec " " na początku drugiego i trzeciego wiersza. Wzorzec nie jest uwzględniony w danych wyjściowych.

    ```csharp
    /**
     * <summary>
     * text </summary>*/
    ```

  - Kompilator nie znajdzie żadnego wspólnego wzorca w następującym komentarzu, ponieważ drugi znak w trzecim wierszu nie jest gwiazdką. W związku z tym cały tekst w drugim i trzecim wierszu jest przetwarzany jako część komentarza.

    ```csharp
    /**
     * <summary>
       text </summary>
    */
    ```

  - Kompilator nie znajdzie żadnego wzorca w następującym komentarzu z dwóch powodów. Po pierwsze, liczba spacji przed gwiazdką nie jest spójna. Po drugie, piąta linia zaczyna się od karty, która nie pasuje do spacji. W związku z tym cały tekst z wierszy od drugiego do piątego jest przetwarzany jako część komentarza.

    <!-- markdownlint-disable MD010 -->
    ```csharp
    /**
      * <summary>
      * text
     *  text2
        *  </summary>
    */
    ```
    <!-- markdownlint-enable MD010 -->

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Komentarze dokumentacji XML](./index.md)
- [-doc (opcje kompilatora C#)](../../language-reference/compiler-options/doc-compiler-option.md)
