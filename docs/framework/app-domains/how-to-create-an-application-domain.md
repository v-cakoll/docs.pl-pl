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
ms.openlocfilehash: 95e5bdbeda4f6faff33467233e28d9dd6bc01d1c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50186936"
---
# <a name="how-to-create-an-application-domain"></a>Porady: tworzenie domeny aplikacji
Typowe host środowiska uruchomieniowego języka automatycznie tworzy domen aplikacji, gdy są potrzebne. Można jednak tworzenie domen aplikacji i ładowania ich te zestawy, które mają być zarządzane osobiście. Można również utworzyć domen aplikacji, z których wykonywanie kodu.  
  
 Tworzenie nowej domeny aplikacji przy użyciu jednej z przeciążonych **createdomain —** metody <xref:System.AppDomain?displayProperty=nameWithType> klasy. Można podać nazwę domeny aplikacji i odwoływać się do niego o takiej nazwie.  
  
 Poniższy przykład tworzy nową domenę aplikacji, przypisuje mu nazwę `MyDomain`, a następnie drukuje nazwę domeny hosta i domeny aplikacji nowo utworzony do konsoli.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
- [Programowanie z domenami aplikacji](application-domains.md#programming-with-application-domains)  
- [Używanie domen aplikacji](../../../docs/framework/app-domains/use.md)
