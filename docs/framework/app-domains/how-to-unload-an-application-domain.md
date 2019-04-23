---
title: 'Instrukcje: Zwolnienie domeny aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Unload method
- application domains, unloading
- unloading application domains
ms.assetid: f356116d-e415-4f7c-a332-6e6a60227192
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3011bd0327440cd04d5eccf5f88c036ddd76267
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212183"
---
# <a name="how-to-unload-an-application-domain"></a>Instrukcje: Zwolnienie domeny aplikacji
Po zakończeniu, przy użyciu domeny aplikacji, zwolnij go za pomocą <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metody. **Zwolnienie** metody bez problemu zmieniała wyłączania domeny określonej aplikacji. W trakcie zwalniania żadne nowe wątki mogą uzyskiwać dostęp do domeny aplikacji, a wszystkie struktury danych specyficzne dla domeny aplikacji są zwalniane.  
  
 Zestawy, ładowane do domeny aplikacji zostaną usunięte i nie są już dostępne. Jeśli zestaw w domenie aplikacji jest niezależne od domeny, dane dla zestawu pozostaje w pamięci, dopóki nie zostanie zamknięta przez cały proces. Nie ma mechanizmu zwolnić zestaw niezależne od domeny inne niż zamykanie cały proces. Istnieją sytuacje, gdy żądanie zwolnienie domeny aplikacji nie będzie działać, a wynikiem <xref:System.CannotUnloadAppDomainException>.  
  
 Poniższy przykład tworzy nową domenę aplikacji o nazwie `MyDomain`drukuje pewnych informacji w konsoli i następnie zwalnia domeny aplikacji. Należy pamiętać, że kod jest podejmuje próbę drukowania przyjazna nazwa niezaładowanej domenie aplikacji w konsoli. Ta akcja generuje wyjątek, który jest obsługiwany przez instrukcje bloku try/catch na końcu program.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie z domenami aplikacji](application-domains.md#programming-with-application-domains)
- [Instrukcje: Tworzenie domeny aplikacji](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)
- [Używanie domen aplikacji](../../../docs/framework/app-domains/use.md)
