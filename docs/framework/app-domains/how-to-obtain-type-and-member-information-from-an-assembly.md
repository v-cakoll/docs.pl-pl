---
title: "Porady: uzyskiwanie informacji dotyczących typów i członków z zestawu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- obtaining assembly information
- assemblies [.NET Framework], obtaining information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1c3112b7484e4d03eaacd218ff8e8ac34e77745b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-obtain-type-and-member-information-from-an-assembly"></a>Porady: uzyskiwanie informacji dotyczących typów i członków z zestawu
<xref:System.Reflection> Przestrzeń nazw zawiera wiele metod uzyskiwania informacji z zestawu. W tej sekcji przedstawiono jednej z tych metod. Aby uzyskać dodatkowe informacje, zobacz [omówienie odbicia](../../../docs/framework/reflection-and-codedom/reflection.md).  
  
 Poniższy przykład uzyskuje informacje o typie i element członkowski z zestawu.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)]
 [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)]
 [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie za pomocą domeny aplikacji](http://msdn.microsoft.com/library/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [Odbicie](../../../docs/framework/reflection-and-codedom/reflection.md)  
 [Używanie domen aplikacji](../../../docs/framework/app-domains/use.md)
