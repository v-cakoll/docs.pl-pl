---
title: 'Instrukcje: Uzyskiwanie informacji dotyczących elementu członkowskiego typów i z zestawu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- obtaining assembly information
- assemblies [.NET Framework], obtaining information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef3fbb7af3097a67cb39f0c3b2ee294b86f0600e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701602"
---
# <a name="how-to-obtain-type-and-member-information-from-an-assembly"></a>Instrukcje: Uzyskiwanie informacji dotyczących elementu członkowskiego typów i z zestawu
<xref:System.Reflection> Przestrzeń nazw zawiera wiele metod uzyskiwanie informacji z zestawu. W tej sekcji przedstawiono jednej z następujących metod. Aby uzyskać więcej informacji, zobacz [Przegląd odbicia](../../../docs/framework/reflection-and-codedom/reflection.md).  
  
 W poniższym przykładzie uzyskano informacje typów i elementów członkowskich z zestawu.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)]
 [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)]
 [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]  
  
## <a name="see-also"></a>Zobacz także
- [Programowanie z domenami aplikacji](./application-domains.md#programming-with-application-domains)
- [Odbicie](../../../docs/framework/reflection-and-codedom/reflection.md)
- [Używanie domen aplikacji](../../../docs/framework/app-domains/use.md)
