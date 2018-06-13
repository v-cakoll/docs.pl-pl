---
title: 'Porady: zwolnienie domeny aplikacji'
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
ms.openlocfilehash: 0a9e5ee865b5e0ac9ec0214a4a0b5194bbcd9f30
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742091"
---
# <a name="how-to-unload-an-application-domain"></a>Porady: zwolnienie domeny aplikacji
Po zakończeniu przy użyciu domeny aplikacji zwolnić ją przy użyciu <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metody. **Zwolnienie** — metoda zamyka bezpieczne domeny określonej aplikacji. Podczas zwalniania nie ma nowych wątków mogą uzyskiwać dostęp do domeny aplikacji i są zwalniane wszystkie struktury dane specyficzne dla domeny aplikacji.  
  
 Zestawy ładowane do domeny aplikacji zostaną usunięte i nie będą już dostępne. Jeśli zestawu w domenie aplikacji jest neutralne dla domen, danych dla zestawu pozostaje w pamięci, dopóki nie zostanie zamknięta przez cały proces. Nie istnieje mechanizm zwolnić zestawem neutralne dla domen innych niż zamykanie cały proces. Istnieją sytuacje, gdy żądanie do wyładować domeny aplikacji nie będzie działać, a powoduje <xref:System.CannotUnloadAppDomainException>.  
  
 Poniższy przykład tworzy nową domenę aplikacji o nazwie `MyDomain`, drukuje niektóre informacje w konsoli, a następnie zwalnia domeny aplikacji. Należy pamiętać, że kod podejmuje próbę drukowania przyjazną nazwę domeny zwolniony aplikacji do konsoli. Ta akcja generuje wyjątek, który jest obsługiwany przez instrukcji try/catch w końcu program.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie za pomocą domeny aplikacji](application-domains.md#programming-with-application-domains)  
 [Instrukcje: tworzenie domeny aplikacji](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 [Używanie domen aplikacji](../../../docs/framework/app-domains/use.md)
