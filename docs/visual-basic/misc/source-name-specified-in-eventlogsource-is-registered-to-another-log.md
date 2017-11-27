---
title: "Nazwa źródła w parametru EventLogSource jest zarejestrowana w dzienniku inną niż określona w EventLogName"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c190caa7634760c2e4dc4a2bb7a9a09f532eb0ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a>Nazwa źródła w parametru EventLogSource jest zarejestrowana w dzienniku inną niż określona w EventLogName
`EventLog` Próbuje odwołać się do źródła, które jest zarejestrowany na inny dziennik. Jeśli piszesz wpisów do dziennika zdarzeń, należy określić <xref:System.Diagnostics.EventLog.Source%2A> właściwości. <xref:System.Diagnostics.EventLog.Source%2A> Właściwość rejestruje składnika z dziennika zdarzeń jako prawidłowe źródło wpisów. Jedno źródło może być skojarzony z (i w związku z tym zapisywanie wpisów do) tylko jeden dziennika zdarzeń w czasie.  
  
 Domyślnie przy próbie zapisu bez najpierw o zarejestrowany składnik jako prawidłowe źródło, system automatycznie rejestruje źródło dziennika zdarzeń, używając wartości <xref:System.Diagnostics.EventLog.Source%2A> właściwość jako ciąg źródła.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, że źródło jest zarejestrowany w dzienniku poprawne. Aby to zrobić, użyj <xref:System.Diagnostics.EventLog.CreateEventSource%2A> metody lub jeden z jego przeciążenia, aby określić ciąg, który unikatowo identyfikuje składnika w dzienniku zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Administrowanie dzienniki zdarzeń](http://msdn.microsoft.com/en-us/35f53238-bdd2-417b-acd8-2fd9f7397f18)  
 [Odwołania do dziennika zdarzeń](http://msdn.microsoft.com/en-us/4af0661c-6c96-49f4-961d-b26ed9bc3e87)  
 [Porady: Dodawanie aplikacji jako źródło wpisów dziennika zdarzeń](http://msdn.microsoft.com/en-us/948ff920-a739-4e66-a191-ee951512d42c)  
 [Porady: usuwanie źródłem zdarzenia](http://msdn.microsoft.com/en-us/bc66c900-4b8a-426a-b8e2-17031a20167e)
