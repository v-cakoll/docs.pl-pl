---
title: Ograniczniki tagów dokumentacji — Przewodnik programowania w języku C#
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: 7e62c75fd393c4009c987830cca41e512cdb6250
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287402"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a>Ograniczniki tagów dokumentacji (Przewodnik programowania w języku C#)

Użycie komentarzy w dokumencie XML wymaga ograniczników wskazujących kompilatorowi, w którym rozpoczyna się i kończą komentarz dokumentacji. Do tagów dokumentacji XML można używać następujących rodzajów ograniczników:

- `///`

  Ogranicznik pojedynczej linii. Jest to formularz, który jest wyświetlany w przykładach dokumentacji i używany przez szablony projektu C#. Jeśli występuje znak spacji po ograniczniku, ten znak nie jest uwzględniany w danych wyjściowych XML.

  > [!NOTE]
  > Zintegrowane środowisko programistyczne (IDE) programu Visual Studio automatycznie wstawia `<summary>` `</summary>` Tagi i i przenosi kursor w tych tagach po wpisaniu `///` ogranicznika w edytorze kodu. Tę funkcję można włączać lub wyłączać w [oknie dialogowym Opcje](/visualstudio/ide/reference/options-text-editor-csharp-advanced).
  
- `/** */`

  Ograniczniki wielowierszowe.

  Podczas używania ograniczników obowiązują pewne reguły formatowania `/** */` :
  
  - W wierszu zawierającym `/**` ogranicznik, jeśli pozostała część wiersza jest białym znakiem, wiersz nie jest przetwarzany dla komentarzy. Jeśli pierwszy znak po `/**` ograniczniku jest znakiem odstępu, oznacza to, że biały znak jest ignorowany, a reszta wiersza jest przetwarzana. W przeciwnym razie cały tekst wiersza po `/**` ograniczniku zostanie przetworzony jako część komentarza.

  - W wierszu zawierającym `*/` ogranicznik, jeśli występuje tylko biały znak do `*/` ogranicznika, ten wiersz jest ignorowany. W przeciwnym razie tekst w wierszu do `*/` ogranicznika jest przetwarzany jako część komentarza.
  
  - Dla wierszy po tym, które zaczyna się od `/**` ogranicznika, kompilator szuka wspólnego wzorca na początku każdego wiersza. Wzorzec może składać się z opcjonalnego odstępu i gwiazdki ( `*` ), po którym następuje bardziej opcjonalny odstęp. Jeśli kompilator odnajdzie wspólny wzorzec na początku każdego wiersza, który nie zaczyna się od `/**` ogranicznika lub `*/` ogranicznika, ignoruje ten wzorzec dla każdego wiersza.

  Poniższe przykłady ilustrują te reguły.

  - Jedyną częścią poniższego komentarza, który jest przetwarzany, jest wiersz zaczynający się od `<summary>` . Trzy formaty tagów dają te same Komentarze.

    ```csharp
    /** <summary>text</summary> */

    /**
    <summary>text</summary>
    */

    /**
     * <summary>text</summary>
    */
    ```

  - Kompilator identyfikuje wspólny wzorzec " \* " na początku drugiego i trzeciego wiersza. Wzorzec nie jest uwzględniony w danych wyjściowych.

    ```csharp
    /**
     * <summary>
     * text </summary>*/
    ```

  - Kompilator nie znalazł wspólnego wzorca w poniższym komentarzu, ponieważ drugi znak w trzecim wierszu nie jest gwiazdką. W związku z tym cały tekst w drugim i trzecim wierszu jest przetwarzany w ramach komentarza.

    ```csharp
    /**
     * <summary>
       text </summary>
    */
    ```

  - Kompilator nie znalazł wzorca w poniższym komentarzu z dwóch przyczyn. Najpierw liczba spacji przed gwiazdką nie jest spójna. Sekunda, piąta linia zaczyna się od karty, która nie jest zgodna z spacjami. W związku z tym cały tekst z wierszy od dwóch do pięciu jest przetwarzany jako część komentarza.

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

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Komentarze dokumentacji XML](./index.md)
- [-doc (opcje kompilatora C#)](../../language-reference/compiler-options/doc-compiler-option.md)
