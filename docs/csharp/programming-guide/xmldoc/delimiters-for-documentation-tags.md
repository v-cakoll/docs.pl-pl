---
title: Ograniczniki tagów dokumentacji - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: c14b0470f7ea488fcb813b68174b5d1cb0d95786
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415588"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a>Ograniczniki tagów dokumentacji (Przewodnik programowania w języku C#)
Użycie komentarze dokumentacji XML wymaga ograniczników, które wskazują kompilatora, gdzie rozpoczyna się i kończy w komentarzu dokumentacji. Za pomocą następujących rodzajów ograniczniki tagów dokumentacji XML:  
  
 `///`  
 Ogranicznik jeden wiersz. Jest to forma, pokazano w przykładach dokumentacji i używane przez Szablony projektu Visual C#. W przypadku biały znak po znaku ograniczającym ten znak nie znajduje się w danych wyjściowych XML.  
  
> [!NOTE]
>  Środowiska IDE programu Visual Studio zawiera funkcję o nazwie inteligentne edytowanie komentarzy, automatycznie wstawi \<podsumowania > i \</summary > Znaczniki i przenosi kursor w ramach tych znaczników po wpisaniu `///` ogranicznika w edytorze kodu . Można włączyć tę funkcję lub wyłączyć [okno dialogowe Opcje](/visualstudio/ide/reference/options-text-editor-csharp-advanced).  
  
 `/** */`  
 Wielowierszowy ograniczników.  
  
 Istnieją pewne reguły formatowania do wykonania, gdy używasz `/** */` ograniczników.  
  
-   W wierszu, który zawiera `/**` ogranicznik, jeśli pozostałą część wiersza jest biały znak, wiersz nie został przetworzony komentarzy. Jeśli pierwszy znak po `/**` ogranicznik jest odstępu, że biały znak jest ignorowana, a pozostała część wiersza jest przetwarzany. W przeciwnym razie cały tekst wiersza po `/**` ogranicznik jest przetwarzany jako część komentarza.  
  
-   W wierszu, który zawiera `*/` ogranicznik, jeśli występuje maksymalnie białych znaków `*/` ogranicznik, w tym wierszu jest ignorowany. W przeciwnym razie tekst w wierszu do `*/` ogranicznik jest przetwarzany jako część komentarza, zgodnie z regułami dopasowywania wzorca opisanego w następny.  
  
-   Wiersze po ten, który rozpoczyna się od `/**` ogranicznik, kompilator szuka wspólny wzorzec na początku każdego wiersza. Wzorzec może zawierać opcjonalny odstęp i znak gwiazdki (`*`), a następnie więcej opcjonalny odstęp. Jeśli kompilator znajdzie wspólny wzorzec na początku każdego wiersza, który nie zaczyna się od `/**` ogranicznik lub `*/` ogranicznika ignoruje tego wzorca dla każdego wiersza.  
  
 Poniższe przykłady ilustrują tych reguł.  
  
-   To jedyna część Poniższy komentarz, które będą przetwarzane jest wiersz, który rozpoczyna się od `<summary>`. Formaty trzech etykiet generuje ten sam komentarzy.  
  
    ```csharp  
    /** <summary>text</summary> */   
  
    /**   
    <summary>text</summary>   
    */   
  
    /**   
     * <summary>text</summary>   
    */  
    ```  
  
-   Kompilator identyfikuje wspólny wzorzec "*" na początku linii drugiego i trzeciego. Wzorzec jest niedostępna w danych wyjściowych.  
  
    ```csharp  
    /**   
     * <summary>   
     * text </summary>*/   
    ```  
  
-   Kompilator znajdzie nie wspólny wzorzec w poniższy komentarz, ponieważ drugim znakiem w trzecim wierszu nie jest znak gwiazdki. W związku z tym cały tekst w wierszach drugiej i trzeciej są przetwarzane w ramach komentarza.  
  
    ```csharp  
    /**   
     * <summary>   
       text </summary>  
    */   
    ```  
  
-   Kompilator znajdzie nie wzorca w poniższy komentarz z dwóch przyczyn. Po pierwsze liczbę spacji przed gwiazdka nie jest spójna. Po drugie piąty wiersz rozpoczyna się od kartę, która jest niezgodna z miejsc do magazynowania. W związku z tym cały tekst z dwóch wierszy, za pośrednictwem pięciu osób są przetwarzane jako część komentarza.  
  
    ```csharp  
    /**   
      * <summary>   
      * text   
     *  text2   
        *  </summary>   
    */   
    ```  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Komentarze dokumentacji XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
- [/ doc (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
- [Komentarze dokumentacji XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
