---
ms.openlocfilehash: 9b184f54650d2efb31ec66f443198b19ceaeb5f3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614706"
---
### <a name="applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a>Aplikacja. FilterMessage nie jest już zgłaszana dla implementacji ponownego wdrożenia IMessageFilter. PreFilterMessage

#### <a name="details"></a>Szczegóły

Przed .NET Framework 4.6.1 Wywoływanie <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> przy użyciu metody <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> wywoływanej <xref:System.Windows.Forms.Application.AddMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=fullName> lub <xref:System.Windows.Forms.Application.RemoveMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=fullName> (a także wywołującej <xref:System.Windows.Forms.Application.DoEvents> ) spowodowałaby wystąpienie <xref:System.IndexOutOfRangeException?displayProperty=fullName> .<p/>Począwszy od aplikacji przeznaczonych dla .NET Framework 4.6.1, ten wyjątek nie jest już zgłaszany i można użyć filtrów ponownie, jak opisano powyżej.

#### <a name="suggestion"></a>Sugestia

Należy pamiętać, że <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> nie będą już raportowane dla zachowań ponownie <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> opisanych powyżej. Ma to wpływ tylko na aplikacje ukierunkowane na .NET Framework 4.6.1. aplikacje ukierunkowane na .NET Framework 4.6.1 mogą zrezygnować z tej zmiany (aplikacje ukierunkowane na starsze platformy mogą wystąpić) przy użyciu przełącznika zgodności [DontSupportReentrantFilterMessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md#mitigation) .

| Nazwa          | Wartość       |
|:--------------|:------------|
| Zakres         | Brzeg        |
| Wersja       | 4.6.1       |
| Typ          | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)?displayProperty=nameWithType>
