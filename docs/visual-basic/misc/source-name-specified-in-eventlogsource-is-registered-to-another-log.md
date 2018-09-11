---
title: Nazwa źródła w parametru EventLogSource została zarejestrowana do dziennika, inne niż określone w EventLogName
ms.date: 07/20/2015
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
ms.openlocfilehash: 03fcc41b0fbb84233aa037d7af17d168050a98b6
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44261054"
---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a>Nazwa źródła w parametru EventLogSource została zarejestrowana do dziennika, inne niż określone w EventLogName
`EventLog` Próbuje do odwoływania się do źródła, który jest zarejestrowany w innym dzienniku. Jeśli piszesz wpisów do dziennika zdarzeń, należy określić <xref:System.Diagnostics.EventLog.Source%2A> właściwości. <xref:System.Diagnostics.EventLog.Source%2A> Właściwość rejestruje składnika z dziennika zdarzeń jako poprawne źródło wpisów. Pojedyncze źródło może być skojarzony z (i w związku z tym zapis wpisów, aby) tylko jeden dziennik zdarzeń w danym momencie.  
  
 Domyślnie, jeśli zostanie podjęta próba zapisu bez po raz pierwszy masz zarejestrowane składnika jako poprawne źródło, system automatycznie rejestruje źródło dziennika zdarzeń, przy użyciu wartości <xref:System.Diagnostics.EventLog.Source%2A> właściwość jako ciąg źródłowy.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, że źródło jest zarejestrowany poprawną dziennika. Aby to zrobić, należy użyć <xref:System.Diagnostics.EventLog.CreateEventSource%2A> metody lub jednej z jej przeciążeń, aby określić ciąg, który unikatowo identyfikuje składnika w dzienniku zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Administrowanie usługą dzienników zdarzeń](https://msdn.microsoft.com/library/35f53238-bdd2-417b-acd8-2fd9f7397f18)  
 [Odwołania do dziennika zdarzeń](https://msdn.microsoft.com/library/4af0661c-6c96-49f4-961d-b26ed9bc3e87)  
 [Porady: Dodawanie aplikacji jako źródło wpisów dziennika zdarzeń](https://msdn.microsoft.com/library/948ff920-a739-4e66-a191-ee951512d42c)  
 [Porady: Usuwanie źródła zdarzeń](https://msdn.microsoft.com/library/bc66c900-4b8a-426a-b8e2-17031a20167e)
