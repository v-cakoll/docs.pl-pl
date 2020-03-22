---
title: 'Rozwiązywanie problemów: odbiorniki logu'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: dd139935dae7fe4d1334b861e6590df29bab7202
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74346854"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a>Rozwiązywanie problemów: odbiorniki logu (Visual Basic)

Można użyć `My.Application.Log` i `My.Log` obiektów do rejestrowania informacji o zdarzeniach występujących w aplikacji.  
  
 Aby ustalić, które detektory dzienników odbierają te wiadomości, zobacz [Przewodnik: Określanie, gdzie informacje o zapisach my.application.log.](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
  
 Obiekt `Log` może użyć filtrowania dziennika, aby ograniczyć ilość informacji, które rejestruje. Jeśli filtry są nieprawidłowo skonfigurowane, dzienniki mogą zawierać nieprawidłowe informacje. Aby uzyskać więcej informacji na temat filtrowania, zobacz [Instruktaż: Filtrowanie danych wyjściowych My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
 Jeśli jednak dziennik jest niepoprawnie skonfigurowany, może być konieczne więcej informacji na temat jego bieżącej konfiguracji. Można uzyskać informacje do tych informacji `TraceSource` za pośrednictwem zaawansowanej właściwości dziennika.  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a>Aby określić detektory dziennika dla obiektu Log w kodzie  
  
1. Zaimportuj <xref:System.Diagnostics> obszar nazw na początku pliku kodu. Aby uzyskać więcej informacji, zobacz [Oświadczenie importu (.NET Obszar nazw i Typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
     [!code-vb[VbVbalrMyApplicationLog#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#13)]  
  
2. Utwórz funkcję, która zwraca ciąg składający się z informacji dla każdego z detektorów dziennika.  
  
     [!code-vb[VbVbalrMyApplicationLog#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#14)]  
  
3. Przekaż kolekcję detektorów śledzenia dziennika do `GetListeners` funkcji i wyświetlić wartość zwracaną.  
  
     [!code-vb[VbVbalrMyApplicationLog#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#19)]  
  
     Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Wskazówki: ustalanie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
