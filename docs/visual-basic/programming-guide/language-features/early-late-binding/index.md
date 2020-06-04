---
title: Wczesne i późne powiązania
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
ms.openlocfilehash: e8d87e095b7c3104e3a2d66525644d1771ae883e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410634"
---
# <a name="early-and-late-binding-visual-basic"></a>Wczesne i późne wiązania (Visual Basic)
Kompilator Visual Basic wykonuje proces wywoływany, `binding` gdy obiekt jest przypisany do zmiennej obiektu. Obiekt jest *wczesnie powiązany* , gdy jest przypisany do zmiennej zadeklarowanej jako określonego typu obiektu. Obiekty wczesnych powiązań umożliwiają kompilatorowi przydzielanie pamięci i wykonywanie innych optymalizacji przed wykonaniem aplikacji. Na przykład poniższy fragment kodu deklaruje zmienną do typu <xref:System.IO.FileStream> :  
  
 [!code-vb[VbVbalrOOP#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#90)]  
  
 Ponieważ <xref:System.IO.FileStream> jest określonym typem obiektu, wystąpienie przypisane do `FS` jest wczesnie powiązane.  
  
 Z kolei obiekt jest *późnie powiązany* , gdy jest przypisany do zmiennej zadeklarowanej jako typu `Object` . Obiekty tego typu mogą zawierać odwołania do dowolnego obiektu, ale nie wiele zalet obiektów wczesnych powiązań. Na przykład poniższy fragment kodu deklaruje zmienną obiektu do przechowywania obiektu zwróconego przez `CreateObject` funkcję:  
  
 [!code-vb[VbVbalrOOP#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/LateBinding.vb#91)]  
  
## <a name="advantages-of-early-binding"></a>Zalety wczesnego wiązania  
 Jeśli jest to możliwe, należy używać obiektów wczesnych powiązań, ponieważ umożliwiają kompilatorowi wykonywanie ważnych optymalizacji, które dają wydajniejsze aplikacje. Obiekty wczesnie powiązane są znacznie szybsze niż obiekty z późnym wiązaniem i ułatwiają odczytywanie i konserwowanie kodu przez poznanie tego, jakiego rodzaju obiekty są używane. Kolejną zaletą wczesnych powiązań jest umożliwienie korzystania z użytecznych funkcji, takich jak automatyczne uzupełnianie kodu i Pomoc dynamiczna, ponieważ zintegrowane środowisko programistyczne (IDE) programu Visual Studio może dokładnie określić typ obiektu, z którym pracujesz podczas edycji kodu. Wczesne powiązanie zmniejsza liczbę i ważność błędów czasu wykonywania, ponieważ umożliwia kompilatorowi raportowanie błędów podczas kompilowania programu.  
  
> [!NOTE]
> Późne wiązanie może być używane tylko w celu uzyskania dostępu do elementów członkowskich typu, które są zadeklarowane jako `Public` . Uzyskiwanie dostępu do składowych zadeklarowanych jako `Friend` lub `Protected Friend` w wyniku błędu czasu wykonywania.  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>
- [Okres istnienia obiektów: w jaki sposób obiekty są tworzone i niszczone](../objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Object — typ danych](../../../language-reference/data-types/object-data-type.md)
