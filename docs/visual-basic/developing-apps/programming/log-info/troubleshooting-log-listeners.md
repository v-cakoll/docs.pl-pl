---
title: "Rozwiązywanie problemów: odbiorniki logu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 14db7019415405af89e9f5e317da617debeb0a19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-log-listeners-visual-basic"></a>Rozwiązywanie problemów: odbiorniki logu (Visual Basic)
Można użyć `My.Application.Log` i `My.Log` obiektów do rejestrowania informacji o zdarzeniach występujących w aplikacji.  
  
 Aby określić, które odbiorniki logu te komunikaty, zobacz [wskazówki: Ustalanie gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
 `Log` Obiektu możesz użyć filtrowania dziennika, aby ograniczyć ilość informacji, które rejestruje. Jeśli filtry są niepoprawnie skonfigurowane, dzienniki mogą zawierać nieprawidłowe informacje. Aby uzyskać więcej informacji dotyczących filtrowania, zobacz [wskazówki: filtrowanie danych wyjściowych My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
 Jednak jeśli dziennik jest niepoprawnie skonfigurowana, może wymagać więcej informacji na temat bieżącej konfiguracji. Aby uzyskać zaawansowane tych informacji za pomocą dziennika `TraceSource` właściwości.  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a>Aby określić odbiorniki dzienników dla obiekt dziennika w kodzie  
  
1.  Importuj <xref:System.Diagnostics> przestrzeni nazw na początku pliku kodu. Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
     [!code-vb[VbVbalrMyApplicationLog#13](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_1.vb)]  
  
2.  Tworzy funkcję, która zwraca ciąg zawierający informacje dla każdego odbiorniki dzienników.  
  
     [!code-vb[VbVbalrMyApplicationLog#14](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_2.vb)]  
  
3.  Kolekcja obiektów nasłuchujących śledzenia dziennika, aby przekazać `GetListeners` funkcji i wyświetlić wartości zwracanej.  
  
     [!code-vb[VbVbalrMyApplicationLog#19](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_3.vb)]  
  
     Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [Wskazówki: Ustalanie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
