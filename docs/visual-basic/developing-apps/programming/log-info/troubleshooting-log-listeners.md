---
title: 'Rozwiązywanie problemów: Odbiorniki logu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: 3d21024a7ebda749f337a95b0fca419b529d2872
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662819"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a>Rozwiązywanie problemów: Odbiorniki logu (Visual Basic)
Możesz użyć `My.Application.Log` i `My.Log` obiekty do rejestrowania informacji o zdarzeniach występujących w aplikacji.  
  
 Aby określić, które odbiorniki logu odebrania tych komunikatów, zobacz [instruktażu: Ustalanie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
 `Log` Obiekt umożliwia filtrowanie dziennika ograniczyć ilość informacji, które rejestruje. Jeśli filtry są nieprawidłowo skonfigurowane, dzienniki mogą zawierać nieprawidłowe informacje. Aby uzyskać więcej informacji na temat filtrowania, zobacz [instruktażu: Filtrowanie danych wyjściowych My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
 Jednak jeśli dziennik jest niepoprawnie skonfigurowana, konieczne może dowiedzieć się więcej o bieżącej konfiguracji. Aby przejść do zaawansowane te informacje za pośrednictwem dziennika `TraceSource` właściwości.  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a>Aby określić odbiorniki logu dla obiektu dziennika w kodzie  
  
1.  Importuj <xref:System.Diagnostics> przestrzeni nazw na początku pliku kodu. Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
     [!code-vb[VbVbalrMyApplicationLog#13](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_1.vb)]  
  
2.  Tworzy funkcję, która zwraca ciąg składający się z informacji dla każdego dziennika odbiorników.  
  
     [!code-vb[VbVbalrMyApplicationLog#14](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_2.vb)]  
  
3.  Kolekcja obiektów nasłuchujących śledzenia dziennika do przekazania `GetListeners` funkcji i wyświetlić wartość zwracaną.  
  
     [!code-vb[VbVbalrMyApplicationLog#19](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_3.vb)]  
  
     Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Przewodnik: Ustalanie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
