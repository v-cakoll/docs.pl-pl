---
title: 'Porady: zwolnienie domeny aplikacji'
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
- Unload method
- application domains, unloading
- unloading application domains
ms.assetid: f356116d-e415-4f7c-a332-6e6a60227192
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 741ddf7c394e1c310e368fe338f71d02a0d4736d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
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
 [Programowanie za pomocą domeny aplikacji](http://msdn.microsoft.com/library/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [Instrukcje: tworzenie domeny aplikacji](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 [Używanie domen aplikacji](../../../docs/framework/app-domains/use.md)
