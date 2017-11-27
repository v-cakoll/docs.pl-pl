---
title: /imports (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e8e9cd761263b3b61a4e6d3e33c5f7f875be7a1d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imports-visual-basic"></a>/imports (Visual Basic)
Importuje przestrzeni nazw z określonego zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```  
/imports:namespaceList  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`namespaceList`|Wymagany. Rozdzielana przecinkami lista obszarów nazw do zaimportowania.|  
  
## <a name="remarks"></a>Uwagi  
 `/imports` Opcja importuje przestrzeni nazw zdefiniowane w obrębie bieżącego zestawu plików źródłowych lub z dowolnej przywoływanego zestawu.  
  
 Elementy członkowskie w przestrzeni nazw określony za pomocą `/imports` są dostępne dla wszystkich plików kodu źródłowego w kompilacji. Użyj [Importy — instrukcja (.NET Namespace i Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) do użycia w pliku kodu źródłowego w jednej przestrzeni nazw.  
  
|Aby ustawić/Import w Visual Studio zintegrowane środowisko programistyczne|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Kliknij przycisk **odwołania** kartę.<br />3.  Wprowadź nazwę przestrzeni nazw w polu obok **dodać importu użytkownika** przycisku.<br />4.  Kliknij przycisk **dodać importu użytkownika** przycisku.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje kiedy `/imports:system` jest określona.  
  
 [!code-vb[VbVbalrCompiler#21](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/imports_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Referencje i Importy — instrukcja](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [Kompilacja przykładów — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
