---
title: Zarządzana wątkowość
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
ms.openlocfilehash: e4c19b664e8fc040fdc4a284b30f6104d676088d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279157"
---
# <a name="managed-threading"></a>Zarządzana wątkowość
Niezależnie od tego, czy tworzysz komputery z jednym procesorem, czy kilka, chcesz, aby aplikacja zapewniała najbardziej reagującą interakcję z użytkownikiem, nawet jeśli aplikacja wykonuje obecnie inne czynności. Korzystanie z wielu wątków wykonywania to jeden z najbardziej zaawansowanych sposobów, aby aplikacja mogła reagować na użytkownika, i w tym samym czasie używa procesora w okresie między lub nawet podczas zdarzeń użytkownika. W tej sekcji przedstawiono podstawowe pojęcia związane z wątkami, które koncentrują się na zarządzanych pojęciach związanych z wątkami i korzystaniu z zarządzanych wątków.  
  
> [!NOTE]
> Począwszy od .NET Framework 4, programowanie wielowątkowe jest znacznie uproszczone przy użyciu <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> klas i <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> , [Parallel LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md), nowych klas kolekcji współbieżnych w <xref:System.Collections.Concurrent?displayProperty=nameWithType> przestrzeni nazw oraz nowy model programowania oparty na koncepcji zadań, a nie w wątkach. Aby uzyskać więcej informacji, zobacz [programowanie równoległe](../parallel-programming/index.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zarządzana wątkowość — podstawy](managed-threading-basics.md)  
 Zawiera omówienie zarządzania wątkami i omówiono, kiedy należy używać wielu wątków.  
  
 [Używanie wątków i wątkowości](using-threads-and-threading.md)  
 Wyjaśnia, jak tworzyć, uruchamiać, wstrzymywać, wznawiać i przerywać wątki.  
  
 [Zarządzana wątkowość — najlepsze rozwiązania](managed-threading-best-practices.md)  
 Omawia poziomy synchronizacji, sposób unikania zakleszczenii i warunków wyścigu oraz inne problemy z wątkami.  
  
 [Wątkowość obiektów i funkcji](threading-objects-and-features.md)  
 Opisuje zarządzane klasy, których można użyć do synchronizowania działań wątków i danych obiektów, do których dostęp odbywa się w różnych wątkach i zawiera Omówienie wątków puli wątków.  
  
## <a name="reference"></a>Dokumentacja  
 <xref:System.Threading>  
 Zawiera klasy służące do korzystania z i synchronizowania zarządzanych wątków.  
  
 <xref:System.Collections.Concurrent>  
 Zawiera klasy kolekcji, które są bezpieczne do użytku z wieloma wątkami.  
  
 <xref:System.Threading.Tasks>  
 Zawiera klasy służące do tworzenia i planowania współbieżnych zadań przetwarzania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Domeny aplikacji](../../framework/app-domains/application-domains.md)  
 Zawiera omówienie domen aplikacji i ich użycia przez Common Language Infrastructure.  
  
 [Asynchroniczne operacje we/wy pliku](../io/asynchronous-file-i-o.md)  
 Opis korzyści związanych z wydajnością oraz podstawowych asynchronicznych operacji We/Wy.  
  
 [Wzorzec asynchroniczny oparty na zadaniach (TAP)](../asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 Zawiera omówienie zalecanego wzorca dla programowania asynchronicznego w programie .NET.  
  
 [Wywołanie metod synchronicznych w sposób asynchroniczny](../asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Wyjaśnia, jak wywoływać metody w wątkach puli wątków przy użyciu wbudowanych funkcji delegatów.  
  
 [Programowanie równoległe](../parallel-programming/index.md)  
 Opisuje równoległe biblioteki programistyczne, które upraszczają korzystanie z wielu wątków w aplikacjach.  
  
 [Równoległe LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md)  
 Opisuje system uruchamiania zapytań równolegle, aby korzystać z wielu procesorów.
