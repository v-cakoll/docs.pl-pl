---
title: Wystąpiły błędy podczas kompilowania schematów XML w projekcie
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 0cc565809792c619ca9903f9ef9b029b51a8aa17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a>Wystąpiły błędy podczas kompilowania schematów XML w projekcie
Wystąpiły błędy podczas kompilowania schematów XML w projekcie. Z tego powodu narzędzie IntelliSense XML nie jest dostępna.  
  
 Istnieje błąd w schemacie definicji schematu XML (XSD) dołączony do projektu. Ten błąd występuje, gdy dodać plik schematu (XSD) XSD, który powoduje konflikt z istniejącą schematu XSD ustawiony dla projektu.  
  
 **Identyfikator błędu:** BC36810  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Kliknij dwukrotnie ikonę ostrzeżenia w **listy błędów** okna. Visual Basic spowoduje przejście do lokalizacji określonej w pliku XSD, który jest źródłem ostrzeżenia. Napraw błąd w schematu XSD.  
  
-   Upewnij się, że wszystkie wymagane pliki XSD schematu (.xsd) znajdują się w projekcie. Może zajść potrzeba kliknięcia przycisku **Pokaż wszystkie pliki** na **projektu** menu, aby zobaczyć XSD Twoje pliki w **Eksploratora rozwiązań**. Kliknij prawym przyciskiem myszy plik XSD, a następnie kliknij przycisk **załącz do projektu** Aby dołączyć plik do projektu.  
  
-   Jeśli używasz XML do kreatora schematu, ten błąd może wystąpić, jeśli wnioskować więcej niż jeden raz schematów z tego samego źródła. W takim przypadku możesz usunąć istniejące pliki schematu XSD z projektu, Dodaj nowe XML do schematu szablonu elementu, a następnie podaj XML do kreatora schematu ze wszystkich odpowiednich źródłami XML dla projektu.  
  
-   Jeśli błąd nie zostanie zidentyfikowana w schematu XSD, kompilator XML może nie mieć wystarczającej ilości informacji zapewnienie szczegółowy komunikat o błędzie. Dzięki temu można uzyskać bardziej szczegółowe informacje o błędzie, jeśli upewnij się, że przestrzenie nazw XML dla plików XSD zawarte w Twojej dopasowania projektu przestrzeni nazw XML dla schematu XML w Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Okno listy błędów](/visualstudio/ide/reference/error-list-window)  
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
