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
ms.openlocfilehash: 4d5f98229c3a9da69a350ae325cd42e8deb6b7bc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119845"
---
# <a name="how-to-unload-an-application-domain"></a>Porady: zwolnienie domeny aplikacji
Po zakończeniu korzystania z domeny aplikacji zwolnij ją przy użyciu metody <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType>. Metoda **Unload** bezpiecznie zamyka określoną domenę aplikacji. W trakcie procesu zwalniania żadne nowe wątki nie mogą uzyskać dostępu do domeny aplikacji, a wszystkie struktury danych specyficzne dla domeny aplikacji są zwolnione.  
  
 Zestawy ładowane do domeny aplikacji są usuwane i nie są już dostępne. Jeśli zestaw w domenie aplikacji jest niezależny od domeny, dane dla zestawu pozostają w pamięci, dopóki cały proces nie zostanie zamknięty. Nie istnieje mechanizm zwalniania zestawu neutralnego z domeną poza zamknięciem całego procesu. Istnieją sytuacje, w których żądanie zwolnienia domeny aplikacji nie działa i skutkuje <xref:System.CannotUnloadAppDomainException>.  
  
 Poniższy przykład tworzy nową domenę aplikacji o nazwie `MyDomain`, drukuje pewne informacje w konsoli, a następnie zwalnia domenę aplikacji. Należy zauważyć, że kod próbuje wydrukować przyjazną nazwę nieładowanej domeny aplikacji do konsoli programu. Ta akcja generuje wyjątek, który jest obsługiwany przez instrukcje try/catch na końcu programu.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie przy użyciu domen aplikacji](application-domains.md#programming-with-application-domains)
- [Instrukcje: tworzenie domeny aplikacji](how-to-create-an-application-domain.md)
- [Używanie domen aplikacji](use.md)
