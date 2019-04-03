---
title: Wystąpiły błędy podczas kompilowania schematów XML w projekcie
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 337fc1fb4dfc83c9b4814d3e45eb0cbe0758f7ce
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842528"
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a>Wystąpiły błędy podczas kompilowania schematów XML w projekcie
Wystąpiły błędy podczas kompilowania schematów XML w projekcie. W związku z tym funkcji IntelliSense XML nie jest dostępna.  
  
 Istnieje błąd w schemacie definicji schematu XML (XSD), zawarty w projekcie. Ten błąd występuje, gdy dodasz plik XSD schematu (XSD), który powoduje konflikt z istniejącego schematu XSD ustawiony dla projektu.  
  
 **Identyfikator błędu:** BC36810  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Kliknij dwukrotnie ikonę ostrzeżenia w **listy błędów** okna. Visual Basic spowoduje przejście do lokalizacji w pliku XSD, który jest źródłem ostrzeżenia. Popraw błąd w schematu XSD.  
  
-   Upewnij się, że wszystkie wymagane pliki schematów (XSD) XSD znajdują się w projekcie. Może być konieczne kliknięcie **Pokaż wszystkie pliki** na **projektu** menu, aby wyświetlić swoje XSD pliki **Eksploratora rozwiązań**. Kliknij prawym przyciskiem myszy plik XSD, a następnie kliknij przycisk **załącz do projektu** dołączenie pliku w projekcie.  
  
-   Jeśli używasz XML do kreatora schematu, ten błąd może wystąpić, jeśli wywnioskować więcej niż jeden raz schematów z tego samego źródła. W takim przypadku możesz usunąć istniejące pliki schematu XSD z projektu, dodać nowe XML do schematu szablonu elementu, a następnie podaj plik XML do kreatora schematu za pomocą wszystkich odpowiednich źródeł XML dla projektu.  
  
-   Jeśli żaden błąd nie zostanie zidentyfikowana w schemacie XSD, kompilator XML może nie mieć wystarczających informacji, aby zapewnić szczegółowy komunikat o błędzie. Dzięki temu można uzyskać bardziej szczegółowe informacje o błędzie, jeśli należy zapewnić, że obszary nazw XML dotyczących XSD plików zawarte w rozgrywki projektu przestrzeni nazw XML dla schematu XML w Visual Studio.  
  
## <a name="see-also"></a>Zobacz także

- [Okno listy błędów](/visualstudio/ide/reference/error-list-window)
- [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
