---
ms.openlocfilehash: 8a1e2ca0790cb62e3c2c879f2ba0bb169ef07d77
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804346"
---
### <a name="applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a>Application.FilterMessage nie rzuca już do ponownego wprowadzania implementacji IMessageFilter.PreFilterMessage

|   |   |
|---|---|
|Szczegóły|Przed programem .NET Framework 4.6.1 <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> wywołanie <xref:System.Windows.Forms.Application.RemoveMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> połączenia z <xref:System.Windows.Forms.Application.DoEvents>wywołanym <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> <xref:System.Windows.Forms.Application.AddMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> <xref:System.IndexOutOfRangeException?displayProperty=name>lub (a jednocześnie wywołaniem) spowodowałoby .<p/>Począwszy od aplikacji przeznaczonych dla platformy .NET Framework 4.6.1, ten wyjątek nie jest już zgłaszany i można użyć filtrów ponownego wnoszenia, jak opisano powyżej.|
|Sugestia|Należy pamiętać, że <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> nie będzie już <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> rzucać dla ponownego uczestnika zachowanie opisane powyżej. Dotyczy to tylko aplikacji docelowych .NET Framework 4.6.1.Aplikacje przeznaczone dla platformy .NET Framework 4.6.1 mogą zrezygnować z tej zmiany (lub aplikacje przeznaczone dla starszych platform mogą wyrazić zgodę) za pomocą przełącznika zgodności [DontSupportReentrantFilMessage.](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md#mitigation)|
|Zakres|Brzeg|
|Wersja|4.6.1|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)?displayProperty=nameWithType></li></ul>|
