---
title: "Wystąpiły błędy podczas kompilowania schematów XML w projekcie"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords: BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07233ed1c68f85878ffdd7131f64e30e158dc350
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
