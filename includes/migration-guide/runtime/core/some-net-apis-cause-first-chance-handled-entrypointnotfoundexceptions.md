---
ms.openlocfilehash: ed526095459a48aa37b585dfed79cc12b9fb9e56
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622139"
---
### <a name="some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a>Niektóre interfejsy API platformy .NET powodują wystąpienie pierwszej szansy (obsłużone) EntryPointNotFoundExceptions

#### <a name="details"></a>Szczegóły

W .NET Framework 4,5 niewielka liczba metod .NET rozpoczęła generowanie pierwszej szansy <xref:System.EntryPointNotFoundException?displayProperty=fullName> s. Te wyjątki zostały obsłużone w .NET Framework, ale mogą przerwać automatyzację testu, która nie oczekiwała na wyjątki pierwszej szansy. Te same interfejsy API przerywają niektóre scenariusze ApiVerifier, gdy HighVersionLie jest włączony.

#### <a name="suggestion"></a>Sugestia

Tę usterkę można uniknąć przez uaktualnienie do .NET Framework 4.5.1. Alternatywnie można zaktualizować automatyzację testową, aby nie przerywać pierwszej szansy <xref:System.EntryPointNotFoundException?displayProperty=fullName> .

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)></li></ul>|
