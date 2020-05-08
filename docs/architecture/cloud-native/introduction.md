---
title: Wprowadzenie do natywnych aplikacji w chmurze
description: Informacje na temat przetwarzania natywnego w chmurze
author: robvet
ms.date: 08/26/2019
ms.openlocfilehash: e1f7683b6f3722bb91e611f199f2e9ce2bbefc63
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895521"
---
# <a name="introduction-to-cloud-native-applications"></a>Wprowadzenie do natywnych aplikacji w chmurze

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Inny dzień w biurze, praca nad "następną wielką rzeczyą".

Pierścienie Cellphone. Jest to Twój przyjazny pracownik, który dzwoni dwa razy dziennie o nowe zadania.

Jednak ten czas jest inny: rozpoczęcie, kapitał i wiele funduszy.

Informacje o technologii w chmurze i rozcięciu są przekazywane przez brzeg.

Szybkie przekazanie do przodu kilku tygodni i jesteś teraz nowym pracownikiem w ramach projektowania sesji projektu dla głównej aplikacji handlu elektronicznego. Zamierzasz konkurować z innymi wiodącymi witrynami handlu elektronicznego.

Jak zostanie on skompilowany?

Jeśli skorzystasz ze wskazówek z ostatnich 15 lat, najprawdopodobniej utworzysz system przedstawiony na rysunku 1,1.

![Tradycyjny wzór monolityczny](./media/monolithic-design.png)

**Rysunek 1-1**. Tradycyjny wzór monolityczny

Tworzysz dużą podstawową aplikację, która zawiera całą logikę domeny. Obejmuje to moduły, takie jak tożsamość, wykaz, porządkowanie i inne. Aplikacja podstawowa komunikuje się z dużą relacyjną bazą danych. Podstawowa funkcja udostępnia funkcje za pośrednictwem interfejsu HTML.

Gratulacje!  Właśnie utworzono aplikację monolityczną.

Nie wszystkie są nieprawidłowe. Monolitów oferują pewne różne zalety. Na przykład są one proste w...

- kompilacja
- test
- Wdrażanie
- troubleshoot
- scale

Wiele pomyślnych aplikacji, które już istnieją, zostały utworzone jako monolitów. Aplikacja jest trafień i w dalszym ciągu rozwija się, iteracji po iteracji, dodając więcej i większą funkcjonalność.

W pewnym momencie można jednak zacząć niewygodnie. Znajdziesz swoje informacje o utracie kontroli nad aplikacją. Po przekroczeniu czasu, całkiem stanie się coraz bardziej intensywne i ostatecznie wprowadzasz stan znany jako **cykl obaw**.

- Aplikacja została tak zaprzeciążona, aby nikt nie zna żadnej osoby.
- Obawiasz się wprowadzać zmiany — każda zmiana ma niezamierzony i kosztowne skutki uboczne.
- Nowe funkcje/poprawki stają się trudne, czasochłonne i kosztowne do wdrożenia.
- Każda wersja jest niewielka, ponieważ może to wymagać pełnego wdrożenia całej aplikacji.
- Jeden niestabilny składnik może spowodować awarię całego systemu.
- Nowe technologie i struktury nie są opcją.
- Trudno jest zaimplementować metody dostarczania Agile.
- W miarę jak baza kodu nie kończy się niekończącymi "szczególnymi przypadkami".
- Konsultanci poinformują Cię o konieczności jego ponownego zapisania.

Wiele organizacji odnosił się do systemu monolitycznej obaw, przyjmując podejście natywne w chmurze do kompilowania systemów. Na rysunku 1-2 przedstawiono ten sam system, w którym zastosowano techniki i praktyki w chmurze.

![Projektowanie natywne w chmurze](./media/cloud-native-design.png)

**Rysunek 1-2**. Projektowanie natywne w chmurze

Zwróć uwagę, jak aplikacja jest rozłożona na zestaw małych, izolowanych mikrousług. Każda usługa jest niezależna i hermetyzuje własny kod, dane i zależności. Każda z nich jest wdrażana w kontenerze oprogramowania i zarządzana przez koordynatora kontenerów. Zamiast dużej relacyjnej bazy danych każda usługa jest właścicielem magazynu danych, którego typ różni się w zależności od potrzeb danych. Zwróć uwagę, jak niektóre usługi zależą od relacyjnej bazy danych, ale inne na NoSQL bazach danych. Jedna usługa przechowuje swój stan w rozproszonej pamięci podręcznej. Zwróć uwagę, jak wszystkie trasy ruchu za pomocą usługi bramy interfejsu API, które są odpowiedzialne za kierowanie ruchu do podstawowych usług zaplecza i wymuszanie wielu zagadnień związanych z wycinaniem. Co najważniejsze, aplikacja w pełni korzysta z funkcji skalowalności i odporności dostępnych w nowoczesnych platformach chmurowych.

### <a name="cloud-native-computing"></a>Przetwarzanie natywne w chmurze

Wygląda... Właśnie korzystamy z tego terminu "*natywne w chmurze*". Po pierwsze myślisz, "co dokładnie robi?" Inna branża Buzzword concocteda przez dostawców oprogramowania w celu wprowadzenia większej ilości informacji?

Na szczęście są znacznie różne i miejmy nadzieję ta książka pomoże Ci przekonać się.

W krótkim czasie natywne chmury stają się trendem w branży oprogramowania. Jest to nowy sposób, aby myśleć o tworzeniu dużych i złożonych systemów, które w pełni wykorzystują nowoczesne rozwiązania do tworzenia oprogramowania, technologie i infrastrukturę chmurową. Podejście zmienia sposób projektowania, implementowania, wdrażania i operacjonalizować systemów.

W przeciwieństwie do ciągłego pogłoskami narosłymiów, które są przeznaczone dla naszych branż, natywne w chmurze to "*for-Real*". Weź pod uwagę [chmurę natywną dla przedsiębiorstw obliczeniowych](https://www.cncf.io/) (CNCF), konsorcjum ponad 300 głównych korporacji z kartą umożliwiającą korzystanie z natywnych rozwiązań w chmurze w różnych technologiach i stosach w chmurze. Jedną z najbardziej potrzebnych grup typu "open source" jest hostowanie wielu najszybszych projektów typu "open source" w witrynie GitHub. Obejmują one takie projekty, jak [Kubernetes](https://kubernetes.io/), [Prometheus](https://prometheus.io/), [Helm](https://helm.sh/), [wysłannika](https://www.envoyproxy.io/)i [gRPC](https://grpc.io/).

CNCF wspiera ekosystem typu "open source" i neutralność dostawcy. Po tym potencjalni klienci przedstawimy zasady, wzorce i najlepsze rozwiązania w chmurze, które są niezależny od technologii. W tym samym czasie omawiamy usługi i infrastrukturę dostępną w chmurze Microsoft Azure na potrzeby tworzenia systemów natywnych w chmurze.

Co dokładnie jest chmurą natywną? Wykorzystaj, niech i Pomóż nam poznać ten nowy świat.

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[Następny](definition.md)
