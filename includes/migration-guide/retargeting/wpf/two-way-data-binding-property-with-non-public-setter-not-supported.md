---
ms.openlocfilehash: 5f1a8af37a305ab0904801002dd99e17e8eca62e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616125"
---
### <a name="two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a>Dwukierunkowe powiązanie danych z właściwością niepubliczną metodą ustawiającą nie jest obsługiwane

#### <a name="details"></a>Szczegóły

Próba utworzenia powiązania danych z właściwością bez publicznej metody ustawiającej nigdy nie była obsługiwanego scenariusza. Począwszy od .NET Framework 4.5.1, ten scenariusz spowoduje zgłoszenie <xref:System.InvalidOperationException?displayProperty=fullName> . Należy zauważyć, że ten nowy wyjątek zostanie wygenerowany tylko dla aplikacji, które mają specjalne miejsce dla .NET Framework 4.5.1. Jeśli aplikacja jest przeznaczona dla .NET Framework 4,5, wywołanie będzie dozwolone. Jeśli aplikacja nie jest ukierunkowana na określoną wersję .NET Framework, powiązanie będzie traktowane jako jednokierunkowe.

#### <a name="suggestion"></a>Sugestia

Aplikacja powinna zostać zaktualizowana w taki sposób, aby korzystała z powiązania jednokierunkowego, albo uwidocznić metodę ustawiającą właściwości publicznie. Alternatywnie, celem .NET Framework 4,5 spowoduje, że aplikacja będzie mieć stare zachowanie.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.5.1       |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType>
