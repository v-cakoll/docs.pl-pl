---
title: 'Instrukcje: Zwolnienie domeny aplikacji'
description: Przeczytaj, jak zwolnić domenę aplikacji w programie .NET przy użyciu metody AppDomain. Unload, aby bezpiecznie zamknąć określoną domenę aplikacji.
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
ms.openlocfilehash: b64a9553f63aa4a8deb57f23a97fa464edd64fee
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104676"
---
# <a name="how-to-unload-an-application-domain"></a>Instrukcje: Zwolnienie domeny aplikacji
Po zakończeniu korzystania z domeny aplikacji zwolnij ją przy użyciu <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metody. Metoda **Unload** bezpiecznie zamyka określoną domenę aplikacji. W trakcie procesu zwalniania żadne nowe wątki nie mogą uzyskać dostępu do domeny aplikacji, a wszystkie struktury danych specyficzne dla domeny aplikacji są zwolnione.  
  
 Zestawy ładowane do domeny aplikacji są usuwane i nie są już dostępne. Jeśli zestaw w domenie aplikacji jest niezależny od domeny, dane dla zestawu pozostają w pamięci, dopóki cały proces nie zostanie zamknięty. Nie istnieje mechanizm zwalniania zestawu neutralnego z domeną poza zamknięciem całego procesu. Istnieją sytuacje, w których żądanie zwolnienia domeny aplikacji nie działa i daje w wyniku <xref:System.CannotUnloadAppDomainException> .  
  
 Poniższy przykład tworzy nową domenę aplikacji o nazwie `MyDomain` , drukuje pewne informacje w konsoli, a następnie zwalnia domenę aplikacji. Należy zauważyć, że kod próbuje wydrukować przyjazną nazwę nieładowanej domeny aplikacji do konsoli programu. Ta akcja generuje wyjątek, który jest obsługiwany przez instrukcje try/catch na końcu programu.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Zobacz też

- [Programowanie przy użyciu domen aplikacji](application-domains.md#programming-with-application-domains)
- [Instrukcje: Tworzenie domeny aplikacji](how-to-create-an-application-domain.md)
- [Używanie domeny aplikacji](use.md)
