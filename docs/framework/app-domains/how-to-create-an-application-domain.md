---
title: 'Porady: tworzenie domeny aplikacji'
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
helpviewer_keywords: application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cdbab5e43d2af7608c4d8322eb071baf591e18d5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
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
 [Programowanie za pomocą domeny aplikacji](http://msdn.microsoft.com/library/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [Używanie domen aplikacji](../../../docs/framework/app-domains/use.md)
