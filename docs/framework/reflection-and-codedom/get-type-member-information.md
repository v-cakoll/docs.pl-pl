---
title: 'Instrukcje: Uzyskiwanie informacji o typie i elemencie członkowskim za pomocą odbicia'
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
author: rpetrusha
ms.author: ronpet
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: da71845ea276267220636cfd661465ea02b2b50d
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972922"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a>Instrukcje: Uzyskiwanie informacji o typie i elemencie członkowskim za pomocą odbicia
<xref:System.Reflection> Przestrzeń nazw zawiera wiele metod uzyskiwania informacji na temat typów i ich członków. W tym artykule przedstawiono jedną z tych metod <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>. Aby uzyskać dodatkowe informacje, zobacz [Omówienie odbicia](reflection.md).
  
## <a name="example"></a>Przykład

Poniższy przykład pobiera informacje o typie i elemencie członkowskim za pomocą odbicia:

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a>Zobacz także

- [Program z domenami aplikacji](../app-domains/application-domains.md#programming-with-application-domains)
- [Odbicie](reflection.md)
- [Korzystanie z domen aplikacji](../app-domains/use.md)
