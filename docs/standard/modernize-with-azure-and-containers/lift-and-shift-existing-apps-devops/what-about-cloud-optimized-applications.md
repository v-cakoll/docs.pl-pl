---
title: "Jakie aplikacje zoptymalizowanych pod kątem chmury?"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Jakie aplikacje zoptymalizowanych pod kątem chmury?"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 40d493196f12af7a5337c47ed85581d933374396
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="what-about-cloud-optimized-applications"></a>Jakie aplikacje zoptymalizowanych pod kątem chmury?

Mimo że zoptymalizowanych pod kątem chmury i [native chmury](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) aplikacje nie podlegają głównym celem tego przewodnika, warto wiedzę na temat tego poziomu dojrzałości modernizacji i odróżnienia go od DevOps gotowe chmury.

Rysunek 4-3 umieszcza aplikacji zoptymalizowanych pod kątem chmury poziomu dojrzałości modernizacji aplikacji:

![Pozycjonowanie aplikacji zoptymalizowanych pod kątem chmury](./media/image3.png)

> **Rysunek 4-3.** Pozycjonowanie aplikacji zoptymalizowanych pod kątem chmury

Poziomu dojrzałości modernizacji zoptymalizowanych pod kątem chmury zwykle wymaga nowych programowanie inwestycji. Przenoszenie poziom zoptymalizowanych pod kątem chmury zwykle wynikają z potrzeb biznesowych do aplikacji, jak to możliwe obniżyć koszty i zwiększyć elastyczność modernizacji i konkurować korzyści. Te cele są realizowane maksymalizując użycie chmury PaaS. Oznacza to nie tylko za pomocą usługi PaaS jak DBaaS, CaaS i przechowywanie jako usługa (STaaS), ale także przy użyciu funkcji migracji do PaaS własne aplikacje i usługi obliczeniowe platform, takich jak usługi Azure App Service lub orchestrators.

Ten typ modernizacji zwykle wymaga refaktoryzacji lub zapisywanie nowy kod, który jest zoptymalizowana pod kątem chmury platformy PaaS (jak dla usługi Azure App Service). Może nawet trzeba zaprojektowanie specjalnie z myślą o środowisku chmury, zwłaszcza, jeśli przenosisz do modeli aplikacji natywnych chmury, które są oparte na mikrousług. Jest to klucz rozróżnianie współczynnik w porównaniu do chmury DevOps gotowe, co wymaga nie przebudowy, a nie nowy kod.

W niektórych przypadkach bardziej zaawansowanych, można utworzyć [native chmury](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) aplikacje oparte na mikrousług architektury, które można rozwijać, elastyczność i skalować do ograniczenia, które mogą być trudne w architekturze wbudowanymi wdrożony w środowisku lokalnym.

Rysunek 4-4 zawiera typ aplikacji, które można wdrożyć, korzystając z modelu zoptymalizowanych pod kątem chmury. Masz dwie podstawowe modern opcji aplikacji i aplikacje natywne chmury.

> ![Typy aplikacji na poziomie zoptymalizowanych pod kątem chmury](./media/image4.png)
>
> **Rysunek 4-4.** Typy aplikacji na poziomie zoptymalizowanych pod kątem chmury

Podstawowe nowoczesnych witryn sieci web, aplikacje i aplikacje natywne chmury można rozszerzyć przez dodanie innych usług, takich jak analizy sztucznego (AI), usługa machine learning (ML) i IoT. Można użyć dowolnego z tych usług do jednej z metod zoptymalizowanych pod kątem chmury można rozszerzyć.

Główną różnicą w aplikacjach na poziomie zoptymalizowanych pod kątem chmury jest w architekturze aplikacji. [Chmura native](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) aplikacje są, zgodnie z definicją w aplikacji, które są oparte na mikrousług. Aplikacje natywne chmury wymagają specjalnych architektury, technologii i platform, w porównaniu do aplikacji sieci web wbudowanymi lub tradycyjny N-poziomowej aplikacji.

Tworzenie nowych aplikacji, które nie używają mikrousług również ma sens. Istnieje wiele scenariuszy nowych i nadal nowoczesnych w których mikrousług metoda może przekroczyć potrzeb. W niektórych przypadkach po prostu można utworzyć aplikacji sieci web wbudowanymi prostsze lub dodawanie coarse-grained usług do aplikacji warstwowych. W takich sytuacjach można nadal prowadzić pełne wykorzystanie chmury PaaS funkcje, takie jak te oferowane przez usługę Azure App Service. Nadal można zmniejszyć pracy konserwacji do limitu.

Ponadto ponieważ tworzenie nowego kodu w scenariuszach zoptymalizowanych pod kątem chmury (pełna aplikacji lub częściowe podsystemów), podczas tworzenia nowego kodu należy używać nowsze wersje programu .NET ([.NET Core](https://docs.microsoft.com/dotnet/core/) i [platformy ASP.NET Core](https://docs.microsoft.com/aspnet/core/), w szczególności). Jest to szczególnie istotne w przypadku utworzenia mikrousług i kontenerów, ponieważ .NET Core framework gotowa i szybki. Zużycie pamięci i szybki start w kontenerach, zostanie wyświetlony, a Twoje aplikacje będą, wysokiej wydajności. Takie podejście jest dopasowany z wymaganiami mikrousług i kontenerów i uzyskać korzyści i platform framework-ich możliwości uruchamiania tej samej aplikacji w systemie Linux, Windows Server i komputerów Mac (Mac dla środowisk deweloperskich).

## <a name="cloud-native-applications-with-cloud-optimized-applications"></a>Aplikacje natywne chmury z aplikacjami zoptymalizowanych pod kątem chmury

[Chmura native](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) jest bardziej zaawansowanych lub dojrzałe stanu dla dużych i kluczowych aplikacji. Aplikacje natywne chmury zwykle wymagają architektury i projektu, które powstały od początku zamiast modernizacji istniejących aplikacji. Klucza różnica między aplikacji natywnych chmury i aplikacji sieci web zoptymalizowanych pod kątem chmury prostsze PaaS wdrożone jest zalecenie, aby używać mikrousług architektury w podejściu native chmury. Zoptymalizowane pod kątem chmury aplikacje mogą być również aplikacje wbudowanymi sieci web lub aplikacje warstwowe wdrożonych w chmurze usługi PaaS, takiej jak usługi Azure App Service.

[Aplikacji współczynnik dwunastu](https://12factor.net/) (kolekcja wzorców, które są ściśle związane ze podejścia mikrousług) również jest uznawany za stanowi wymóg dla [native chmury](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) architekturach aplikacji.

[Foundation natywnego obliczeniowych w chmurze (CNCF)](https://www.cncf.io/) jest podstawowy promotor zasad native chmury. Firma Microsoft [członkiem CNCF](https://azure.microsoft.com/blog/announcing-cncf/).

Dla definicji próbki oraz więcej informacji na temat aplikacji natywnych chmury, zobacz artykuł Gartner [projektowania i zaprojektować aplikacje natywne chmury](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications). Dokładne wskazówki firmy Microsoft dotyczące sposobu wdrażania aplikacji natywnych chmury, zobacz [mikrousług .NET: Architektura konteneryzowanych aplikacji .NET](https://aka.ms/microservicesebook).

Najważniejszym czynnikiem wziąć pod uwagę, czy migrować do pełnego zastosowania [native chmury](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) model jest możesz ponownie należy zaprojektować do architektura mikrousług. Wymaga to wyraźnie znaczącą inwestycję w rozwoju ze względu na duże proces refaktoryzacji. Ta opcja jest zazwyczaj wybrany dla kluczowych aplikacji wymagających nowe poziomy skalowalność i elastyczność długoterminowej. Jednak można pomyśleć kierunku native chmury przez dodanie mikrousług dla kilku nowych scenariuszy, a ostatecznie Refaktoryzuj aplikacji pełni jako mikrousług. Jest to przyrostowe metody, która jest najlepszym rozwiązaniem w przypadku niektórych scenariuszy.

## <a name="what-about-microservices"></a>Co mikrousług? 

Ważne jest zrozumienie mikrousług oraz ich współdziałaniu, gdy rozważane jest chmury natywne aplikacje dla swojej organizacji.

Architektura mikrousług jest zaawansowane metody, która służy do aplikacji, które są tworzone od początku lub rozwijać istniejących aplikacji (lokalnej lub gotowe DevOps aplikacji w chmurze) kierunku aplikacje natywne chmury. Można uruchomić, dodając kilka mikrousług do istniejących aplikacji, aby dowiedzieć się o nowych wzorcami mikrousług. Jednak wyraźnie, musisz architektów i kod, szczególnie w przypadku tego typu architektura.

Jednak mikrousług nie są wymagane dla każdej nowej lub nowoczesnych aplikacji. Mikrousług nie są "magic bullet", a nie są jednej, najlepszym sposobem tworzenia każdej aplikacji. Jak i kiedy korzystać mikrousług zależy od typu aplikacji, która jest potrzebne do tworzenia.

Architektura mikrousług staje się to preferowane rozwiązanie dla rozproszonych i dużych lub złożonych aplikacji krytycznym, które są oparte na wiele niezależnych podsystemów w formie autonomicznej usługi. W architektura mikrousług aplikacji jest utworzony jako zbiór usług, które można niezależnie rozwinięte, przetestowane, wersji, wdrożyć i skalowania. Może to obejmować wszystkie powiązane, autonomicznej bazy danych na mikrousługi.

Aby uzyskać szczegółowy widok architektury mikrousług, które można wdrożyć przy użyciu platformy .NET Core, zobacz e-book do pobrania plików PDF [mikrousług .NET: Architektura konteneryzowanych aplikacji .NET](https://aka.ms/microservicesebook). Przewodnik jest również dostępna [online](https://docs.microsoft.com/dotnet/standard/microservices-architecture/).

Ale nawet w scenariuszach, w których mikrousług oferują zaawansowane możliwości niezależne od wdrożenia, granice silne podsystemu i różnorodności technologii-też wiązać wiele wyzwania. Wyzwania dotyczące projektowanie aplikacji rozproszonych, takich jak modeli danych pofragmentowanych i niezależny; uzyskanie odporność komunikacji między mikrousług; potrzebę spójność ostateczna; i złożoność działania. Mikrousług wprowadzenie wyższy poziom złożoności w porównaniu do tradycyjnego wbudowanymi aplikacjami.

Ze względu na złożoność architektury mikrousług tylko konkretnych scenariuszy i niektórych typów aplikacji są odpowiednie dla aplikacji opartych na mikrousługi. Obejmują one dużych i złożonych aplikacji, które mają wiele rozwijającymi podsystemy. W takich przypadkach warto pomyśleć bardziej złożonych architektura oprogramowania, zwiększyć elastyczność długoterminowej i bardziej efektywną obsługę aplikacji. Ale dla mniej złożonymi scenariuszami, mogą być lepiej kontynuować podejście wbudowanymi aplikacji lub zbliża się do N-warstwowa prostsze.

Jako ostatecznego Uwaga, nawet ryzyko jest powtarzających się o to pojęcie nie powinien wyglądać za pomocą mikrousług w aplikacji jako "kwoty ujęte lub nic we wszystkich*.*" Można rozszerzać i rozwijać istniejące aplikacje wbudowanymi, dodając nowe, małe scenariusze oparte na mikrousług. Nie trzeba zacząć od początku, aby rozpocząć pracę z podejścia architektura mikrousług. W rzeczywistości zaleca się, że rozwijać z używania istniejącej aplikacji wbudowanymi lub N-warstwowa przez dodanie nowych scenariuszy. Po pewnym czasie można podzielić aplikacji w autonomicznej części lub mikrousług. Możesz przystąpić do zmieniających się wbudowanymi aplikacji w kierunku mikrousług krok po kroku.

## <a name="when-to-use-azure-app-service-for-modernizing-existing-net-apps"></a>Kiedy należy używać usługi Azure App Service modernizacji istniejących aplikacji .NET

Gdy użytkownik modernizacji istniejących aplikacji sieci web ASP.NET do poziomu dojrzałości zoptymalizowanych pod kątem chmury, ponieważ opracowywaniu aplikacji sieci web przy użyciu programu .NET Framework, głównego zależności są w systemach Windows i najprawdopodobniej Internet Information Server (IIS). Można użyć i wdrażania aplikacji systemu Windows i usług IIS albo przez wdrożenie bezpośrednio do [usłudze Azure App Service](https://docs.microsoft.com/azure/app-service/app-service-value-prop-what-is) lub przy pierwszym containerizing aplikacji przy użyciu kontenery systemu Windows. Jeśli containerizing, wdrożyć aplikacje albo Windows kontenery hostów (na podstawie maszyny Wirtualnej) lub sieci szkieletowej usług Azure klastra obsługującego kontenery systemu Windows.

Gdy używasz kontenery systemu Windows, otrzymasz z zalet przechowywanie w kontenerach. Zwiększyć elastyczność w wysyłki i wdrażanie aplikacji i zmniejszyć tarcia problemów środowiska (przemieszczania, tworzenie/testowanie oprogramowania produkcyjnego). W kolejnych sekcjach kilka rozszerzana na temat korzyści, które można uzyskać od przy użyciu kontenerów.

Przeprowadzonych podczas opracowywania tego przewodnika, usługa aplikacji Azure nie obsługuje kontenery systemu Windows. Obsługuje kontenery dla systemu Linux. Dlatego może być dalej pytanie "Jak wybrać między usługi aplikacji Azure i kontenery systemu Windows?"

Zasadniczo jeśli działa usługa Azure App Service dla aplikacji i nie ma żadnego serwera niestandardowych zależności blokuje ścieżka do użycia usługi aplikacji, należy przeprowadzić migrację istniejąca aplikacja sieci web .NET do usługi App Service. To najprostszy, najbardziej efektywny sposób Obsługa aplikacji. Na platformie Azure aplikacji również ma uprościć ścieżkę konserwacji z powodu korzyści z PaaS infrastruktury, takich jak DBaaS, CaaS i STaaS.

Jednak jeśli aplikacja serwera lub zależności niestandardowych, które nie są obsługiwane w usłudze Azure App Service, być może należy wziąć pod uwagę opcje, które są oparte na kontenery systemu Windows. Serwera lub zależności niestandardowych Przykładami oprogramowania innych firm lub plik msi, który musi zostać zainstalowany na serwerze, ale który nie jest obsługiwany w usłudze Azure App Service. Innym przykładem jest inna konfiguracja serwera, która nie jest obsługiwana w usłudze Azure App Service, takie jak korzystanie z zestawów w globalnej pamięci podręcznej zestawów (GAC) lub COM / składniki modelu COM +. Dzięki użyciu obrazów kontenera systemu Windows mogą zawierać zależności niestandardowych w tym samym "jednostka wdrożenia."

Alternatywnie można Refaktoryzuj obszary aplikacji, które nie są obsługiwane przez usługę Azure App Service. W zależności od ilości pracy refaktoryzacji są wymagane, będzie musiał dokładnie ocenić, czy który warto.

### <a name="benefits-of-moving-to-azure-app-service"></a>Korzyści przechodzenia do usługi Azure App Service

Usługa aplikacji Azure jest pełni zarządzane rozwiązanie typu PaaS oferty, które ułatwia tworzenie aplikacji sieci web, które bazują na procesy biznesowe. Korzystając z usługi aplikacji, można uniknąć kosztów zarządzania infrastruktury skojarzone uaktualniania i obsługa sieci web aplikacji lokalnych. W szczególności Wytnij sprzętu i koszty licencjonowania działających w sieci web aplikacji lokalnych.

Jeśli aplikacja sieci web jest odpowiedni w przypadku migracji do usługi Azure App Service, główne korzyści jest krótkim czas potrzebny do przenoszenia aplikacji. Usługa App Service oferuje bardzo proste środowisko, w którym można rozpocząć pracę.

Usługa aplikacji Azure jest najlepszym rozwiązaniem w przypadku większości aplikacji sieci web, ponieważ jest najprostsza PaaS na platformie Azure, który służy do uruchomienia aplikacji sieci web. Wdrażania i zarządzania są zintegrowane z platformy, Lokacje szybko skalować do obsługi obciążeń dużego natężenia ruchu sieciowego i zapewnia wysoką dostępność, Menedżera ruchu i równoważenie obciążenia wbudowanych.

Nawet monitorowanie aplikacji sieci web jest proste, za pomocą usługi Azure Application Insights. Usługi Application Insights jest dostępna bezpłatnie z usługi aplikacji i nie wymaga specjalnych kod w aplikacji. Uruchom aplikację sieci web w usłudze App Service, a uzyskasz atrakcyjnych system monitorowania z żadne dodatkowe czynności.

Z usługi aplikacji można również bezpośrednio wiele aplikacji open source z galerii aplikacji sieci Web platformy Azure (na przykład WordPress lub Umbraco), lub można utworzyć nowej lokacji za pomocą framework i narzędzia wybranych przez użytkownika, takich jak ASP.NET. Funkcja aplikacji usługi z zadań Webjob ułatwia Dodaj zadanie w tle przetwarzania do aplikacji sieci web usługi aplikacji.

Kluczowe zalety migracji aplikacji sieci web za pomocą funkcji aplikacji sieci Web w usłudze Azure App Service są następujące:

-   Automatyczne skalowanie, aby spełnić wymagania podczas dużego obciążenia i ograniczyć koszty poza godzinami cichy.

-   Automatyczne tworzenie kopii zapasowych do ochrony danych i zmiany.

-   Wysokiej dostępności i odporności na platformie Azure PaaS.

-   Miejsca wdrożenia dla rozwoju i środowiska przejściowe i testowania wielu projektów witryny.

-   Równoważenie obciążenia i ochrony Distributed Denial of Service (DDoS).

-   Zarządzanie ruchem przekierować użytkowników do najbliższego geograficzne wdrożenia.

Chociaż usługi aplikacji może być najlepszym rozwiązaniem dla nowej aplikacji sieci web, jednak dla istniejących aplikacji usługi aplikacji może być najlepszym wyborem tylko wtedy, gdy zależności aplikacji są obsługiwane w usłudze App Service.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Analiza zgodności w usłudze Azure App Service**  
[https://www.migratetoazure.NET/Resources](https://www.migratetoazure.net/Resources)


### <a name="benefits-of-moving-to-windows-containers"></a>Korzyści polegające na przeniesieniu do kontenerów systemu Windows

Głównego zaletą używania kontenery systemu Windows jest, aby uzyskać bardziej niezawodne i ulepszone wdrażanie środowisko, w porównaniu do aplikacji z systemem innym niż konteneryzowanych. Ponadto o aplikacji modernizowana z kontenerami skutecznie sprawia, że aplikacji teraz wiele platform i chmury, które obsługuje kontenery systemu Windows. Korzyści polegające na przeniesieniu do kontenerów systemu Windows są opisane bardziej szczegółowo w kolejnych sekcjach.

Środowiska obliczeniowe głównej w programie Azure (w ogólnodostępnej, począwszy od połowy 2017) obsługujących kontenery systemu Windows są sieć szkieletowa usług Azure i podstawowych hostów kontenery systemu Windows (Windows Server 2016 maszyn wirtualnych). Tych środowisk są scenariusze głównego infrastruktury w tym przewodniku.

Można także wdrożyć kontenery systemu Windows na innych orchestrators, takich jak Kubernetes, DC/OS lub Docker Swarm. Obecnie (przypada wcześniej 2017), tych platform się w wersji zapoznawczej usługi kontenera platformy Azure przy użyciu kontenery systemu Windows.

>[!div class="step-by-step"]
[Poprzednie](microsoft-technologies-in-cloud-devops-ready-applications.md)
[dalej](how-to-deploy-existing-net-apps-to-azure-app-service.md)
