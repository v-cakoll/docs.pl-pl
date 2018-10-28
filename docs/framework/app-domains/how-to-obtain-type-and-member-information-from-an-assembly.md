---
title: 'Porady: uzyskiwanie informacji dotyczących typów i członków z zestawu'
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
ms.openlocfilehash: 44fcded298f33a420a505900f618c1c67f4b9b6f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180065"
---
# <a name="how-to-obtain-type-and-member-information-from-an-assembly"></a>Porady: uzyskiwanie informacji dotyczących typów i członków z zestawu
<xref:System.Reflection> Przestrzeń nazw zawiera wiele metod uzyskiwanie informacji z zestawu. W tej sekcji przedstawiono jednej z następujących metod. Aby uzyskać więcej informacji, zobacz [Przegląd odbicia](../../../docs/framework/reflection-and-codedom/reflection.md).  
  
 W poniższym przykładzie uzyskano informacje typów i elementów członkowskich z zestawu.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)]
 [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)]
 [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]  
  
## <a name="see-also"></a>Zobacz też  
- [Programowanie z domenami aplikacji](./application-domains.md#programming-with-application-domains)
- [Odbicie](../../../docs/framework/reflection-and-codedom/reflection.md)  
- [Używanie domen aplikacji](../../../docs/framework/app-domains/use.md)
