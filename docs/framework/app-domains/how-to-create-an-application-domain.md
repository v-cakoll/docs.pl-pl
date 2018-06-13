---
title: 'Porady: tworzenie domeny aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c579c97e273e7d3e149e04f7aa7670313663b617
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751781"
---
# <a name="how-to-create-an-application-domain"></a>Porady: tworzenie domeny aplikacji
Typowe host czasu wykonywania języka automatycznie tworzy domeny aplikacji, gdy są potrzebne. Można jednak tworzenie domeny aplikacji i załadować do nich te zestawy, które mają być zarządzane osobiście. Można też utworzyć, z których wykonanie kodu domeny aplikacji.  
  
 Tworzenie nowej domeny aplikacji przy użyciu jednej z przeciążone **CreateDomain** metod w <xref:System.AppDomain?displayProperty=nameWithType> klasy. Należy podać nazwę domeny aplikacji i odwołaj się o takiej nazwie.  
  
 Poniższy przykład tworzy nową domenę aplikacji, przypisuje mu nazwę `MyDomain`, a następnie drukuje nazwę domeny hosta i domeny podrzędnej nowo utworzonej aplikacji do konsoli.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie za pomocą domeny aplikacji](application-domains.md#programming-with-application-domains)  
 [Używanie domen aplikacji](../../../docs/framework/app-domains/use.md)
