---
title: 'Instrukcje: uzyskiwanie informacji o typie i elemencie członkowskim za pomocą odbicia'
description: Dowiedz się, jak uzyskać informacje o typie i elemencie członkowskim za pomocą odbicia przy użyciu przestrzeni nazw System. odbicie.
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: fa7af39c0addb328944a03236c26982301caf722
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865323"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a>Instrukcje: uzyskiwanie informacji o typie i elemencie członkowskim za pomocą odbicia
<xref:System.Reflection>Przestrzeń nazw zawiera wiele metod uzyskiwania informacji na temat typów i ich członków. W tym artykule przedstawiono jedną z tych metod <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> . Aby uzyskać dodatkowe informacje, zobacz [Omówienie odbicia](reflection.md).
  
## <a name="example"></a>Przykład

Poniższy przykład pobiera informacje o typie i elemencie członkowskim za pomocą odbicia:

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a>Zobacz także

- [Program z domenami aplikacji](../app-domains/application-domains.md#programming-with-application-domains)
- [Odbicie](reflection.md)
- [Korzystanie z domen aplikacji](../app-domains/use.md)
