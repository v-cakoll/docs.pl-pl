---
title: Nazwa źródła w parametru EventLogSource została zarejestrowana do dziennika, inne niż określone w EventLogName
ms.date: 07/20/2015
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
ms.openlocfilehash: 22129ab0c4f7fe0a78300907a949d9368028c9fa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61595000"
---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a>Nazwa źródła w parametru EventLogSource została zarejestrowana do dziennika, inne niż określone w EventLogName
`EventLog` Próbuje do odwoływania się do źródła, który jest zarejestrowany w innym dzienniku. Jeśli piszesz wpisów do dziennika zdarzeń, należy określić <xref:System.Diagnostics.EventLog.Source%2A> właściwości. <xref:System.Diagnostics.EventLog.Source%2A> Właściwość rejestruje składnika z dziennika zdarzeń jako poprawne źródło wpisów. Pojedyncze źródło może być skojarzony z (i w związku z tym zapis wpisów, aby) tylko jeden dziennik zdarzeń w danym momencie.  
  
 Domyślnie, jeśli zostanie podjęta próba zapisu bez po raz pierwszy masz zarejestrowane składnika jako poprawne źródło, system automatycznie rejestruje źródło dziennika zdarzeń, przy użyciu wartości <xref:System.Diagnostics.EventLog.Source%2A> właściwość jako ciąg źródłowy.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że źródło jest zarejestrowany poprawną dziennika. Aby to zrobić, należy użyć <xref:System.Diagnostics.EventLog.CreateEventSource%2A> metody lub jednej z jej przeciążeń, aby określić ciąg, który unikatowo identyfikuje składnika w dzienniku zdarzeń.  
  
## <a name="see-also"></a>Zobacz także

- [Administrowanie usługą dzienników zdarzeń](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/4f69axw4(v=vs.90))
- [Odwołania do dziennika zdarzeń](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/k43k9z2a(v=vs.90))
- [Instrukcje: Dodaj aplikację jako źródło wpisów dziennika zdarzeń](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/xz73e171(v=vs.90))
- [Instrukcje: Usuń źródła zdarzeń](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/k57466fc(v=vs.90))
