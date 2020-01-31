---
title: Ograniczniki tagów dokumentacji — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: dd4ddb3b324bd6d235efb541c90875dbe9ed4c2d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789832"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a>Ograniczniki tagów dokumentacji (C# Przewodnik programowania)

Użycie komentarzy w dokumencie XML wymaga ograniczników wskazujących kompilatorowi, w którym rozpoczyna się i kończą komentarz dokumentacji. Do tagów dokumentacji XML można używać następujących rodzajów ograniczników:

- `///`

  Ogranicznik pojedynczej linii. Jest to formularz, który jest wyświetlany w przykładach dokumentacji i używany przez szablony C# projektu wizualnego. Jeśli występuje znak spacji po ograniczniku, ten znak nie jest uwzględniany w danych wyjściowych XML.

  > [!NOTE]
  > Środowisko IDE programu Visual Studio ma funkcję o nazwie edytowanie komentarzy inteligentnych, która automatycznie wstawia > podsumowania \<i \</Summary > Tagi i przenosi kursor w tych tagach po wpisaniu ogranicznika `///` w edytorze kodu. Tę funkcję można włączać lub wyłączać w [oknie dialogowym Opcje](/visualstudio/ide/reference/options-text-editor-csharp-advanced).
  
- `/** */`

  Ograniczniki wielowierszowe.

  W przypadku używania ograniczników `/** */` istnieją pewne reguły formatowania:
  
  - W wierszu zawierającym ogranicznik `/**`, jeśli pozostała część wiersza jest białym znakiem, wiersz nie jest przetwarzany dla komentarzy. Jeśli pierwszy znak po ograniczniku `/**` jest białym znakiem, oznacza to, że odstęp jest ignorowany, a pozostała część wiersza jest przetwarzana. W przeciwnym razie cały tekst wiersza po przekroczeniu ogranicznika `/**` jest przetwarzany jako część komentarza.

  - W wierszu zawierającym ogranicznik `*/`, jeśli występuje tylko białe miejsce do ogranicznika `*/`, ten wiersz jest ignorowany. W przeciwnym razie tekst w wierszu do ogranicznika `*/` jest przetwarzany jako część komentarza, zgodnie z regułami dopasowywania wzorców opisanymi w następującym punkcie.
  
  - Dla linii po tej, która rozpoczyna się od ogranicznika `/**`, kompilator szuka wspólnego wzorca na początku każdego wiersza. Wzorzec może składać się z opcjonalnego odstępu i gwiazdki (`*`), po którym następuje bardziej opcjonalny odstęp. Jeśli kompilator odnajdzie wspólny wzorzec na początku każdego wiersza, który nie zaczyna się od ogranicznika `/**` lub ogranicznika `*/`, zignoruje ten wzorzec dla każdego wiersza.

  Poniższe przykłady ilustrują te reguły.

  - Jedyną częścią poniższego komentarza, który zostanie przetworzony, jest wiersz zaczynający się od `<summary>`. Trzy formaty tagów dają te same Komentarze.

    ```csharp
    /** <summary>text</summary> */

    /**
    <summary>text</summary>
    */

    /**
     * <summary>text</summary>
    */
    ```

  - Kompilator identyfikuje wspólny wzorzec "\*" na początku drugiego i trzeciego wiersza. Wzorzec nie jest uwzględniony w danych wyjściowych.

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

- [C#Przewodnik programowania](../index.md)
- [Komentarze dokumentacji XML](./index.md)
- [-doc (C# opcje kompilatora)](../../language-reference/compiler-options/doc-compiler-option.md)
