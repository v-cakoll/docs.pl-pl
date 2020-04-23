---
title: 'Instrukcje: uzyskiwanie informacji o typie i elemencie członkowskim za pomocą odbicia'
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: 9ffc173bbd0ed12eedea0c191f6d39baf181793a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130214"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a>Instrukcje: uzyskiwanie informacji o typie i elemencie członkowskim za pomocą odbicia
<xref:System.Reflection> Przestrzeń nazw zawiera wiele metod uzyskiwania informacji na temat typów i ich członków. W tym artykule przedstawiono jedną z tych metod <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>. Aby uzyskać dodatkowe informacje, zobacz [Omówienie odbicia](reflection.md).
  
## <a name="example"></a>Przykład

Poniższy przykład pobiera informacje o typie i elemencie członkowskim za pomocą odbicia:

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a>Zobacz też

- [Program z domenami aplikacji](../app-domains/application-domains.md#programming-with-application-domains)
- [Odbicie](reflection.md)
- [Korzystanie z domen aplikacji](../app-domains/use.md)
