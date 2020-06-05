---
title: 'Rozwiązywanie problemów: odbiorcy dzienników'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: 8d2d8294d9e9bb42d72fe4f6c37bf846bd644907
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398321"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a>Rozwiązywanie problemów: odbiorniki logu (Visual Basic)

Za pomocą `My.Application.Log` obiektów i można `My.Log` rejestrować informacje o zdarzeniach występujących w aplikacji.  
  
 Aby określić, które detektory dzienników odbierają te komunikaty, zobacz [Przewodnik: Określanie, gdzie my. Application. Log zapisuje informacje](walkthrough-determining-where-my-application-log-writes-information.md).  
  
 `Log`Obiekt może korzystać z filtrowania dzienników w celu ograniczenia ilości informacji, które rejestruje. Jeśli filtry są nieprawidłowo skonfigurowane, dzienniki mogą zawierać nieprawidłowe informacje. Aby uzyskać więcej informacji na temat filtrowania, zobacz [Przewodnik: filtrowanie danych wyjściowych my. Application. log](walkthrough-filtering-my-application-log-output.md).  
  
 Jeśli jednak dziennik jest niepoprawnie skonfigurowany, może być konieczne więcej informacji na temat jego bieżącej konfiguracji. Te informacje można uzyskać, korzystając z właściwości zaawansowane dziennika `TraceSource` .  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a>Aby określić detektory dzienników dla obiektu dziennika w kodzie  
  
1. Zaimportuj <xref:System.Diagnostics> przestrzeń nazw na początku pliku kodu. Aby uzyskać więcej informacji, zobacz [Imports — Instrukcja (przestrzeń nazw i typ .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
     [!code-vb[VbVbalrMyApplicationLog#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#13)]  
  
2. Utwórz funkcję zwracającą ciąg składający się z informacji dla każdego z odbiorników dziennika.  
  
     [!code-vb[VbVbalrMyApplicationLog#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#14)]  
  
3. Przekaż kolekcję detektorów śledzenia dziennika do `GetListeners` funkcji i wyświetl wartość zwracaną.  
  
     [!code-vb[VbVbalrMyApplicationLog#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#19)]  
  
     Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Praca z dziennikami aplikacji](working-with-application-logs.md)
- [Przewodnik: ustalanie lokalizacji, w której element My.Application.Log zapisuje informacje](walkthrough-determining-where-my-application-log-writes-information.md)
