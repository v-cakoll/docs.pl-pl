---
title: 'Instrukcje: Tworzenie domeny aplikacji'
description: Zapoznaj się z tematem jak utworzyć domenę aplikacji w programie .NET. Możesz utworzyć domenę aplikacji, aby załadować zestawy do zarządzania osobiście, lub utwórz je do wykonania kodu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
ms.openlocfilehash: 8e44e682f64854dbc0181b26f6ed3fa2905b7814
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104812"
---
# <a name="how-to-create-an-application-domain"></a>Instrukcje: Tworzenie domeny aplikacji
Host środowiska uruchomieniowego języka wspólnego automatycznie tworzy domeny aplikacji, gdy są potrzebne. Można jednak tworzyć własne domeny aplikacji i ładować je do tych zestawów, które mają być zarządzane osobiście. Możesz również utworzyć domeny aplikacji, z których wykonywany jest kod.  
  
 Tworzysz nową domenę aplikacji przy użyciu jednej **z przeciążonych** metod w <xref:System.AppDomain?displayProperty=nameWithType> klasie. Możesz nadać domenie aplikacji nazwę i odwołać się do niej przy użyciu tej nazwy.  
  
 Poniższy przykład tworzy nową domenę aplikacji, przypisuje jej nazwę `MyDomain` , a następnie drukuje nazwę domeny hosta i nowo utworzoną domenę podrzędnej aplikacji do konsoli programu.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz też

- [Programowanie przy użyciu domen aplikacji](application-domains.md#programming-with-application-domains)
- [Używanie domeny aplikacji](use.md)
