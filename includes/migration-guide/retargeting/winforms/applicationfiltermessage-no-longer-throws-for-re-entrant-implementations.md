---
ms.openlocfilehash: 8a1e2ca0790cb62e3c2c879f2ba0bb169ef07d77
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757810"
---
### <a name="applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a>Application.FilterMessage nie zgłasza już wielobieżnej implementacji IMessageFilter.PreFilterMessage

|   |   |
|---|---|
|Szczegóły|Przed użytkownikiem programu .NET Framework 4.6.1, wywoływania <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> z <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> której wywołać <xref:System.Windows.Forms.Application.AddMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> lub <xref:System.Windows.Forms.Application.RemoveMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> (podczas wywoływania również <xref:System.Windows.Forms.Application.DoEvents>) spowodowałoby <xref:System.IndexOutOfRangeException?displayProperty=name>.<p/>Począwszy od aplikacji przeznaczonych dla platformy .NET Framework 4.6.1 to nie jest już wyjątku, a filtry wielobieżnej zgodnie z powyższym opisem mogą być używane.|
|Sugestia|Należy pamiętać, że <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> nie będzie już zgłaszać dla wielobieżnej <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> zachowanie opisane powyżej. Dotyczy to tylko aplikacji przeznaczonych dla środowiska .NET Framework 4.6.1.Apps przeznaczonych dla platformy .NET Framework 4.6.1 można zrezygnować z tej zmiany (lub określania wartości docelowej struktury starsze zrezygnować w aplikacji) za pomocą [DontSupportReentrantFilterMessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md#mitigation) Przełącznik zgodności.|
|Zakres|Krawędź|
|Wersja|4.6.1|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)?displayProperty=nameWithType></li></ul>|
