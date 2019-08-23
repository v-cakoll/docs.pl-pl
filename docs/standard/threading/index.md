---
title: Zarządzana wątkowość
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 763646bfb358b8e5faf13a14f2facb98f855b5c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913283"
---
# <a name="managed-threading"></a>Zarządzana wątkowość
Niezależnie od tego, czy tworzysz komputery z jednym procesorem, czy kilka, chcesz, aby aplikacja zapewniała najbardziej reagującą interakcję z użytkownikiem, nawet jeśli aplikacja wykonuje obecnie inne czynności. Korzystanie z wielu wątków wykonywania to jeden z najbardziej zaawansowanych sposobów, aby aplikacja mogła reagować na użytkownika, i w tym samym czasie używa procesora w okresie między lub nawet podczas zdarzeń użytkownika. W tej sekcji przedstawiono podstawowe pojęcia związane z wątkami, które koncentrują się na zarządzanych pojęciach związanych z wątkami i korzystaniu z zarządzanych wątków.  
  
> [!NOTE]
> Począwszy od .NET Framework 4, <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> programowanie wielowątkowe jest znacznie uproszczone przy użyciu klas i <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> , [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md) <xref:System.Collections.Concurrent?displayProperty=nameWithType> , nowych klas kolekcji współbieżnych w przestrzeni nazw oraz nowe programowanie Model oparty na koncepcji zadań, a nie w wątkach. Aby uzyskać więcej informacji, zobacz [programowanie równoległe](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zarządzana wątkowość — podstawy](../../../docs/standard/threading/managed-threading-basics.md)  
 Zawiera omówienie zarządzania wątkami i omówiono, kiedy należy używać wielu wątków.  
  
 [Używanie wątków i wątkowości](../../../docs/standard/threading/using-threads-and-threading.md)  
 Wyjaśnia, jak tworzyć, uruchamiać, wstrzymywać, wznawiać i przerywać wątki.  
  
 [Zarządzana wątkowość — najlepsze rozwiązania](../../../docs/standard/threading/managed-threading-best-practices.md)  
 Omawia poziomy synchronizacji, sposób unikania zakleszczenii i warunków wyścigu oraz inne problemy z wątkami.  
  
 [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)  
 Opisuje zarządzane klasy, których można użyć do synchronizowania działań wątków i danych obiektów, do których dostęp odbywa się w różnych wątkach i zawiera Omówienie wątków puli wątków.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Threading>  
 Zawiera klasy służące do korzystania z i synchronizowania zarządzanych wątków.  
  
 <xref:System.Collections.Concurrent>  
 Zawiera klasy kolekcji, które są bezpieczne do użytku z wieloma wątkami.  
  
 <xref:System.Threading.Tasks>  
 Zawiera klasy służące do tworzenia i planowania współbieżnych zadań przetwarzania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Domeny aplikacji](../../../docs/framework/app-domains/application-domains.md)  
 Zawiera omówienie domen aplikacji i ich użycia przez Common Language Infrastructure.  
  
 [Asynchroniczne operacje We/Wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md)  
 Opis korzyści związanych z wydajnością oraz podstawowych asynchronicznych operacji We/Wy.  
  
 [Wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 Zawiera omówienie zalecanego wzorca dla programowania asynchronicznego w programie .NET.  
  
 [Wywoływanie metod synchronicznych w sposób asynchroniczny](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Wyjaśnia, jak wywoływać metody w wątkach puli wątków przy użyciu wbudowanych funkcji delegatów.  
  
 [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)  
 Opisuje równoległe biblioteki programistyczne, które upraszczają korzystanie z wielu wątków w aplikacjach.  
  
 [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 Opisuje system uruchamiania zapytań równolegle, aby korzystać z wielu procesorów.
