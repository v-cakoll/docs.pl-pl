---
title: 'Rozwiązywanie problemów: Odbiorniki logu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: f2dba14ed883b428e47b71533bcb51506167fd49
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979011"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a>Rozwiązywanie problemów: Odbiorniki logu (Visual Basic)
Możesz użyć `My.Application.Log` i `My.Log` obiekty do rejestrowania informacji o zdarzeniach występujących w aplikacji.  
  
 Aby określić, które odbiorniki logu odebrania tych komunikatów, zobacz [instruktażu: Ustalanie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
 `Log` Obiekt umożliwia filtrowanie dziennika ograniczyć ilość informacji, które rejestruje. Jeśli filtry są nieprawidłowo skonfigurowane, dzienniki mogą zawierać nieprawidłowe informacje. Aby uzyskać więcej informacji na temat filtrowania, zobacz [instruktażu: Filtrowanie danych wyjściowych My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
 Jednak jeśli dziennik jest niepoprawnie skonfigurowana, konieczne może dowiedzieć się więcej o bieżącej konfiguracji. Aby przejść do zaawansowane te informacje za pośrednictwem dziennika `TraceSource` właściwości.  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a>Aby określić odbiorniki logu dla obiektu dziennika w kodzie  
  
1.  Importuj <xref:System.Diagnostics> przestrzeni nazw na początku pliku kodu. Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
     [!code-vb[VbVbalrMyApplicationLog#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#13)]  
  
2.  Tworzy funkcję, która zwraca ciąg składający się z informacji dla każdego dziennika odbiorników.  
  
     [!code-vb[VbVbalrMyApplicationLog#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#14)]  
  
3.  Kolekcja obiektów nasłuchujących śledzenia dziennika do przekazania `GetListeners` funkcji i wyświetlić wartość zwracaną.  
  
     [!code-vb[VbVbalrMyApplicationLog#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#19)]  
  
     Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Przewodnik: Ustalanie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
