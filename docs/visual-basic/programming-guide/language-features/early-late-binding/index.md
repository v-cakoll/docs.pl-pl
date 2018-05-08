---
title: Wczesne i późne powiązania (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- objects [Visual Basic], late-bound
- objects [Visual Basic], early-bound
- objects [Visual Basic], late bound
- early binding [Visual Basic], Visual Basic compiler
- binding [Visual Basic], late and early
- objects [Visual Basic], early bound
- Visual Basic compiler, early and late binding
- late binding [Visual Basic]
- late binding [Visual Basic], Visual Basic compiler
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
ms.openlocfilehash: 8426899b0c0d3649f47cbd6ad5383dd3c95b9499
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="early-and-late-binding-visual-basic"></a>Wczesne i późne powiązania (Visual Basic)
Kompilator Visual Basic wykonuje w procesie nazywanym `binding` gdy obiekt jest przypisany do zmiennej obiektu. Obiekt *z wczesnym wiązaniem* zadeklarowany gdy jest przypisany do zmiennej typu określonego obiektu. Wczesne obiektów powiązanych Zezwalaj kompilatora można przydzielić pamięci i wykonywać inne optymalizacje przed wykonaniem aplikacji. Na przykład poniższy fragment kodu deklaruje zmienną typu <xref:System.IO.FileStream>:  
  
 [!code-vb[VbVbalrOOP#90](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_1.vb)]  
  
 Ponieważ <xref:System.IO.FileStream> jest określonego typu obiektu, wystąpienia przypisany do `FS` jest z wczesnym wiązaniem.  
  
 Z kolei jest obiekt *Rozpoznanie późnego wiązania* zadeklarowany gdy jest przypisany do zmiennej typu `Object`. Obiekty tego typu można przechowywania odwołań do dowolnego obiektu, ale nie mają wiele zalet obiektów z wczesnym wiązaniem. Na przykład poniższy fragment kodu deklaruje zmienną obiektu do przechowywania obiektu zwróconego przez `CreateObject` funkcji:  
  
 [!code-vb[VbVbalrOOP#91](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_2.vb)]  
  
## <a name="advantages-of-early-binding"></a>Zalety wczesne powiązania  
 Obiekty z wczesnym wiązaniem, jeśli to możliwe, należy użyć, ponieważ umożliwiają one kompilator w celu optymalizacji ważne, które zwracają większą wydajność aplikacji. Z wczesnym wiązaniem obiekty są znacznie szybsze niż obiekty z późnym wiązaniem i upewnij kodu łatwiej odczytywać i obsługa poprzez podanie dokładnie jakiego rodzaju obiektów są używane. Inną zaletą do wczesnego wiązania jest przydatne funkcje, takie jak uzupełnianie kodu automatyczne i Pomoc dynamiczna ponieważ Visual Studio zintegrowane środowisko programistyczne (IDE) można określić dokładnie typ obiektu pracujesz w trakcie edycji Kod. Wczesne powiązania ogranicza liczbę i ważność błędów czasu wykonywania, ponieważ umożliwia kompilatorowi przesłania raportów o błędach, gdy program ma być kompilowana.  
  
> [!NOTE]
>  Późne wiązanie tylko umożliwia dostęp do elementów członkowskich typu, które są zadeklarowane jako `Public`. Uzyskiwanie dostępu do elementów członkowskich zadeklarowany jako `Friend` lub `Protected Friend` powoduje błąd w czasie wykonywania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>  
 [Okres istnienia obiektów: w jaki sposób obiekty są tworzone i niszczone](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 [Object, typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)
