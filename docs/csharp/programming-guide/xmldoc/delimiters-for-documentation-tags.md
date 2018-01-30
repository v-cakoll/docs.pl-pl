---
title: "Ograniczniki tagów dokumentacji (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0c72ee03ff8a2e28bec1ba83e42cd7f201b140ed
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a>Ograniczniki tagów dokumentacji (Przewodnik programowania w języku C#)
Korzystanie z komentarze w dokumencie XML wymaga ograniczników, które wskazują w kompilatorze, gdzie komentarzy dokumentacji rozpoczęcia i zakończenia. Można użyć następujące rodzaje ograniczniki tagów dokumentacji XML:  
  
 `///`  
 Ogranicznik jeden wiersz. Jest to formularz, który jest wyświetlany w przykładach dokumentacji i używane przez Szablony projektów Visual C#. W przypadku biały znak po znaku ograniczającym ten znak nie jest uwzględniony w danych wyjściowych XML.  
  
> [!NOTE]
>  Środowiska IDE programu Visual Studio ma funkcję inteligentne komentarz edycji automatycznie wstawiany \<podsumowania > i \</summary > Znaczniki i przesuwa kursor w ramach tych tagów po wpisaniu `///` ogranicznik w edytorze kodu . Można włączyć tę funkcję lub wyłączyć [opcje — Okno dialogowe](/visualstudio/ide/reference/options-text-editor-csharp-advanced).  
  
 `/** */`  
 Wielowierszowy ograniczników.  
  
 Brak niektórych reguł formatowania, które należy wykonać, korzystając z `/** */` ograniczników.  
  
-   W wierszu, który zawiera `/**` ogranicznik, jeśli do końca wiersza jest białe, wiersz nie został przetworzony przeznaczone do komentarzy. Jeśli pierwszym znakiem po `/**` ogranicznik jest białe, czy biały znak jest ignorowane, a pozostałe wiersz jest przetwarzany. W przeciwnym razie cały tekst wiersza po `/**` ogranicznik jest przetwarzany jako część komentarza.  
  
-   W wierszu, który zawiera `*/` ogranicznik, jeśli istnieje tylko biały znak do `*/` ogranicznika wiersza jest ignorowana. W przeciwnym razie tekst w wierszu do `*/` ogranicznik jest przetwarzany jako część komentarza, opisane w poniższych punktor zasadom dopasowywanie do wzorca.  
  
-   Po tym, który rozpoczyna się od linii `/**` ogranicznik, kompilator szuka wspólnego wzorca na początku każdego wiersza. Wzorzec może zawierać białych opcjonalne i znak gwiazdki (`*`), a następnie opcjonalnie biały znak. Jeśli kompilator znajdzie wspólnego wzorca na początku każdego wiersza, który nie zaczyna się od `/**` ogranicznik lub `*/` ogranicznika ignoruje tego wzorca dla każdego wiersza.  
  
 Poniższe przykłady przedstawiają te reguły.  
  
-   Tylko część następujące komentarz, który zostanie przetworzona jest wiersza, który rozpoczyna się od `<summary>`. Trzy formaty utworzyć samą komentarze.  
  
    ```  
    /** <summary>text</summary> */   
  
    /**   
    <summary>text</summary>   
    */   
  
    /**   
     * <summary>text</summary>   
    */  
    ```  
  
-   Kompilator identyfikuje typowe wzorzec "*" na początku linii drugiego i trzeciego. Wzorzec nie jest uwzględniony w danych wyjściowych.  
  
    ```  
    /**   
     * <summary>   
     * text </summary>*/   
    ```  
  
-   Kompilator znajduje nie wspólnego wzorca w poniższy komentarz, ponieważ znak na trzeci wiersz nie jest znak gwiazdki. W związku z tym cały tekst w wierszach drugiego i trzeciego są przetwarzane w ramach komentarza.  
  
    ```  
    /**   
     * <summary>   
       text </summary>  
    */   
    ```  
  
-   Kompilator znajduje nie wzorca w komentarzu następujących dwóch powodów. Po pierwsze liczbę spacji przed gwiazdka nie jest spójna. Drugie piątej wiersz rozpoczyna się od kartę, która jest niezgodna z spacji. W związku z tym cały tekst z dwa wiersze, za pomocą pięciu są przetwarzane w ramach komentarza.  
  
    ```  
    /**   
      * <summary>   
      * text   
     *  text2   
        *  </summary>   
    */   
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Komentarze dokumentacji XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
 [/ doc (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [Komentarze dokumentacji XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
