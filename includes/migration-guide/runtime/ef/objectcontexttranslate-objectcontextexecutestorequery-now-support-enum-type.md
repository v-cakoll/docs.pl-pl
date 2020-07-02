---
ms.openlocfilehash: 6af8e97423c04abca25feb8d77ea9ab6e198a4f0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620328"
---
### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a>Obiekt ObjectContext. tłumaczenia i ObjectContext.ExecuteStoreQuery teraz obsługują typ wyliczeniowy

#### <a name="details"></a>Szczegóły

W .NET Framework 4,0 parametr generyczny <code>T</code> <code>ObjectContext.Translate</code> i metody nie <code>ObjectContext.ExecuteStoreQuery</code> mogą być wyliczeniem. Ten scenariusz jest teraz obsługiwany.

#### <a name="suggestion"></a>Sugestia

Jeśli polecenie Przetłumacz lub ExecuteStoreQuery zostało wywołane w typie wyliczeniowym w .NET Framework 4,0, zwrócono wartość "0". W przypadku pożądanego zachowania, wywołania powinny być zastępowane stałą 0 (lub równoważnej wyliczeniu).

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|
