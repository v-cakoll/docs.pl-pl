---
title: "Budowanie odpornej usługi gotowe do chmury. Dążenie przejściowych błędów w chmurze"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Budowanie odpornej usługi gotowe do chmury. Dążenie przejściowych błędów w chmurze"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 9c21ae37ad2e4fc318eb4b206069db7662bfc5d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>Budowanie odpornej usługi gotowe do chmury: dążenie przejściowych błędów w chmurze 

Odporność jest możliwość skutków błędów i kontynuować działanie. Odporność nie jest o unikanie błędów, ale akceptowania fakt, że wystąpią błędy i następnie odpowiada na żądania je w taki sposób, który pozwala uniknąć przestoju lub utraty danych. Celem odporności jest do zwrócenia aplikacji w pełni funkcjonalnej stan po awarii.

Aplikacja jest gotowa do chmury, gdy co najmniej implementuje model opartych na oprogramowaniu odporności, a nie w modelu oparte na sprzęcie. Aplikacji w chmurze musi obejmować częściowe błędów, które na pewno nastąpi. Należy zaprojektować lub częściowo Refaktoryzuj aplikacji, jeśli chcesz uzyskać odporność na awarie częściowe oczekiwanego. Powinny być zaprojektowane do radzenia sobie z częściowa błędami, takie jak awarie sieci i węzły lub awarii w chmurze maszyn wirtualnych. Kontenery nawet przenoszony do innego węzła w klastrze orchestrator może spowodować krótkich błędami okresowymi w aplikacji.

## <a name="handling-partial-failure"></a>Obsługa częściowej awarii

W aplikacji opartej na chmurze istnieje ryzyko wszechobecne częściowej awarii. Na przykład wystąpienie jedną witrynę sieci Web lub kontener może się nie powieść lub może być niedostępny lub nie odpowiada przez krótki czas. Lub z jednej maszyny Wirtualnej lub serwerem mogą ulec awarii.

Ponieważ klienci i usługi są osobne procesy, usługa nie może być stanie odpowiedzieć w odpowiednim czasie żądania klienta. Usługa może być przeciążona i bardzo wolno odpowiadać na żądania lub ją po prostu nie mogą być niedostępne przez krótki czas z powodu problemów dotyczących sieci.

Rozważmy na przykład wbudowanymi aplikacji .NET, który uzyskuje dostęp do bazy danych w bazie danych SQL Azure. Jeśli baza danych Azure SQL lub innych usług innych firm nie odpowiada na krótki czas (bazy danych Azure SQL mogą być przeniesione do innego węzła lub serwera i nie odpowiadać przez kilka sekund), gdy użytkownik spróbuje wykonać żadnych działań, mogą ulec awarii aplikacji i Pokaż w wyjątek bardzo jednocześnie.

Podobny scenariusz może wystąpić w aplikacji, która korzysta z usług HTTP. Sieci lub samej usługi mogą nie być dostępne w chmurze podczas krótkich, przejściowy błąd.

Odporność aplikacji, tak jak pokazano w rysunek 4 — 9 należy zaimplementować technik, takich jak "ponawia próbę z wykładniczego wycofywania" w celu daje aplikacji możliwość obsługi błędów przejściowych w zasobach. Należy również użyć "obwód podziałów" w aplikacji. Wyłącznika zatrzymuje aplikacji próby uzyskania dostępu do zasobu, gdy jest rzeczywiście długotrwałą awarię. Używając wyłącznika aplikacji pozwala uniknąć zdolnemu odmowa usługi do samej siebie.

![Błędy częściowe obsługiwane przez liczbę ponownych prób z wykładniczego wycofywania](./media/image9.png)

> **Rysunek 4-9.** Błędy częściowe obsługiwane przez liczbę ponownych prób z wykładniczego wycofywania

Te techniki można użyć zarówno w zasobach HTTP, jak i w bazie danych zasobów. 4 rysunek-9, aplikacja jest oparty na architekturze 3-warstwowej, więc należy te techniki na poziomie usługi (HTTP) i na poziomie warstwy danych (TCP). W wbudowanymi aplikacji, która używa tylko jednej aplikacji warstwę oprócz bazy danych (nie dodatkowych usług lub mikrousług) Obsługa przejściowe błędy na poziomie połączenia bazy danych może być wystarczająca. W takim scenariuszu zwykle określoną konfigurację połączenia bazy danych jest wymagana.

Podczas wdrażania dostępu do bazy danych, w zależności od wersji platformy .NET, używane są odporne komunikacji może być bardzo proste (na przykład [z programu Entity Framework 6 lub nowszym](https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx), jest wystarczy Konfigurowanie połączenie z bazą danych). Lub może być konieczne korzystać z dodatkowych bibliotek, takich jak [bloku aplikacji obsługi błędów przejściowych](https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx) (w przypadku wcześniejszych wersji programu .NET) lub nawet wdrożenia własnej biblioteki.

Podczas implementowania ponownych prób HTTP i podziałów obwód, dla platformy .NET zaleca się użycie [Polly](https://github.com/App-vNext/Polly) biblioteki, która .NET 4.0, .NET 4.5 i .NET Standard 1.1, które obsługuje .NET Core.

Informacje na temat wdrożenie strategii dotyczące postępowania z częściowa błędów w chmurze, zobacz następujące odwołania.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Implementowanie odporność komunikacji do obsługi błędów w częściowej**

    [https://docs.microsoft.com/DotNet/Standard/microservices-Architecture/Implement-resilient-Applications/Partial-failure-Strategies](https://docs.microsoft.com/dotnet/standard/microservices-architecture/implement-resilient-applications/partial-failure-strategies)

-   **Entity Framework połączenia odporności i spróbuj ponownie logiki (wersja 6 i nowsze)**

    [https://msdn.microsoft.com/en-us/library/dn456835 (v=vs.113).aspx](https://msdn.microsoft.com/en-us/library/dn456835(v=vs.113).aspx)

-   **W bloku aplikacji obsługi błędu przejściowego**

<!-- -->

-   [https://msdn.microsoft.com/en-us/library/hh680934 (v=pandp.50).aspx](https://msdn.microsoft.com/en-us/library/hh680934(v=pandp.50).aspx)

-   **Biblioteka Polly odporność komunikacji HTTP**

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
[Poprzednie](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[dalej](modernize-your-apps-with-monitoring-and-telemetry.md)
