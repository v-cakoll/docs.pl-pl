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
ms.openlocfilehash: 83bf0ad96b352ed5c015723dd89aee7913d2a88e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119884"
---
# <a name="how-to-create-an-application-domain"></a>Porady: tworzenie domeny aplikacji
Host środowiska uruchomieniowego języka wspólnego automatycznie tworzy domeny aplikacji, gdy są potrzebne. Można jednak tworzyć własne domeny aplikacji i ładować je do tych zestawów, które mają być zarządzane osobiście. Możesz również utworzyć domeny aplikacji, z których wykonywany jest kod.  
  
 Tworzysz nową domenę aplikacji przy użyciu jednej **z przeciążonych** metod w klasie <xref:System.AppDomain?displayProperty=nameWithType>. Możesz nadać domenie aplikacji nazwę i odwołać się do niej przy użyciu tej nazwy.  
  
 Poniższy przykład tworzy nową domenę aplikacji, przypisuje jej nazwę `MyDomain`, a następnie drukuje nazwę domeny hosta i nowo utworzoną domenę podrzędnej aplikacji do konsoli programu.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie przy użyciu domen aplikacji](application-domains.md#programming-with-application-domains)
- [Używanie domen aplikacji](use.md)
