---
title: Wczesne i późne wiązania (Visual Basic)
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
ms.openlocfilehash: d05322ba831aac6173ac9d7fa7f369a208b676d0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965377"
---
# <a name="early-and-late-binding-visual-basic"></a>Wczesne i późne wiązania (Visual Basic)
Kompilator Visual Basic wykonuje proces wywoływany `binding` , gdy obiekt jest przypisany do zmiennej obiektu. Obiekt jest *wczesnie powiązany* , gdy jest przypisany do zmiennej zadeklarowanej jako określonego typu obiektu. Obiekty wczesnych powiązań umożliwiają kompilatorowi przydzielanie pamięci i wykonywanie innych optymalizacji przed wykonaniem aplikacji. Na przykład poniższy fragment kodu deklaruje zmienną do typu <xref:System.IO.FileStream>:  
  
 [!code-vb[VbVbalrOOP#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#90)]  
  
 Ponieważ <xref:System.IO.FileStream> jest określonym typem obiektu, wystąpienie przypisane do `FS` jest wczesnie powiązane.  
  
 Z kolei obiekt jest późnie *powiązany* , gdy jest przypisany do zmiennej zadeklarowanej jako typu `Object`. Obiekty tego typu mogą zawierać odwołania do dowolnego obiektu, ale nie wiele zalet obiektów wczesnych powiązań. Na przykład poniższy fragment kodu deklaruje zmienną obiektu do przechowywania obiektu zwróconego przez `CreateObject` funkcję:  
  
 [!code-vb[VbVbalrOOP#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/LateBinding.vb#91)]  
  
## <a name="advantages-of-early-binding"></a>Zalety wczesnego wiązania  
 Jeśli jest to możliwe, należy używać obiektów wczesnych powiązań, ponieważ umożliwiają kompilatorowi wykonywanie ważnych optymalizacji, które dają wydajniejsze aplikacje. Obiekty wczesnie powiązane są znacznie szybsze niż obiekty z późnym wiązaniem i ułatwiają odczytywanie i konserwowanie kodu przez poznanie tego, jakiego rodzaju obiekty są używane. Kolejną zaletą wczesnych powiązań jest umożliwienie korzystania z użytecznych funkcji, takich jak automatyczne uzupełnianie kodu i Pomoc dynamiczna, ponieważ zintegrowane środowisko programistyczne (IDE) programu Visual Studio może dokładnie określić typ obiektu, z którym pracujesz podczas edycji kodu. Wczesne powiązanie zmniejsza liczbę i ważność błędów czasu wykonywania, ponieważ umożliwia kompilatorowi raportowanie błędów podczas kompilowania programu.  
  
> [!NOTE]
> Późne wiązanie może być używane tylko w celu uzyskania dostępu do elementów członkowskich `Public`typu, które są zadeklarowane jako. Uzyskiwanie dostępu do `Friend` składowych zadeklarowanych jako lub `Protected Friend` w wyniku błędu czasu wykonywania.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>
- [Okres istnienia obiektu: Jak obiekty są tworzone i niszczone](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Object, typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)
