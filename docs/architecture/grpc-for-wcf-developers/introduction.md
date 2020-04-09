---
title: Wprowadzenie - gRPC dla programistów WCF
description: Wprowadzenie
ms.date: 09/02/2019
ms.openlocfilehash: 41f470eb02a77b1b6a26a7d4c2ca347ad07d828d
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988937"
---
# <a name="introduction"></a>Wprowadzenie

Pomaganie maszynom w komunikowaniu się ze sobą było jednym z głównych troski ery cyfrowej. W szczególności podejmowane są ciągłe wysiłki w celu określenia optymalnego mechanizmu komunikacji zdalnej, który będzie odpowiadał wymaganiom interoperacyjności obecnej infrastruktury. Jak można sobie wyobrazić, że mechanizm zmienia się jako wymagania lub infrastruktury ewoluuje.

Wydanie programu .NET Core 3.0 oznacza zmianę sposobu, w jaki firma Microsoft dostarcza rozwiązania do komunikacji zdalnej deweloperom, którzy chcą świadczyć usługi na różnych platformach. .NET Core nie oferuje Windows Communication Foundation (WCF) po wyjęciu z pudełka, ale wraz z wydaniem ASP.NET Core 3.0 zapewnia wbudowaną funkcjonalność gRPC.

gRPC jest popularnym frameworkiem w szerszej społeczności oprogramowania. Jest używany przez deweloperów w wielu językach programowania dla nowoczesnych scenariuszy RPC. Społeczność i ekosystem są żywe i aktywne. Obsługa protokołu gRPC jest dodawana do składników infrastruktury, takich jak Kubernetes, siatki usług, moduły równoważenia obciążenia i inne. Te czynniki, wraz z jego wydajności, wydajności i kompatybilności między platformami, sprawiają, że gRPC jest naturalnym wyborem dla nowych aplikacji i aplikacji WCF przechodzących do .NET Core.

## <a name="history"></a>Historia

Podstawowa zasada sieci komputerowej jako nic więcej niż grupa komputerów wymiany danych ze sobą w celu osiągnięcia zestawu powiązanych ze sobą zadań nie zmieniła się od momentu jej powstania. Ale złożoność, skala i oczekiwania wzrosły wykładniczo.  

W latach 90., nacisk położono głównie na poprawę sieci wewnętrznych, które używały tego samego języka i platform. TCP/IP stał się złotym standardem dla tego typu komunikacji.

Wkrótce skupiono się na tym, jak najlepiej zoptymalizować komunikację na wielu platformach, promując podejście oparte na języku. Architektura zorientowana na usługi (SOA) zapewniła strukturę luźnego sprzężenia szerokiego zbioru usług, które mogłyby być dostarczone do aplikacji.

Rozwój *usług internetowych* nastąpił, gdy wszystkie główne platformy mogły uzyskać dostęp do Internetu, ale nadal nie mogły ze sobą współpracować. Usługi sieci Web mają otwarte standardy i protokoły, w tym:

- XML do oznaczania i kodowanie danych.
- Protokół SOAP (Simple Object Access Protocol) do przesyłania danych.
- Język definicji usług sieci Web (WSDL) do opisywania i łączenia usług sieci web z aplikacjami klienckimi.
- Uniwersalny opis, odnajdywanie i integracja (UDDI), aby usługi sieci web były wykrywalne przez inne usługi.

PROTOKÓŁ SOAP definiuje reguły, za pomocą których rozproszone elementy aplikacji mogą komunikować się ze sobą, nawet jeśli są one na różnych platformach. MYDŁO jest oparte na XML, więc jest czytelny dla człowieka. Ofiarą za uczynienie MYDŁA łatwym do zrozumienia jest rozmiar; Wiadomości PROTOKOŁU SOAP są większe niż wiadomości w porównywalnych protokołach. Usługa SOAP została zaprojektowana w celu podziału aplikacji monolitycznych na wieloskładnikową formę bez utraty bezpieczeństwa ani kontroli. WCF został zaprojektowany do pracy z tego rodzaju systemem, w przeciwieństwie do gRPC, który rozpoczął się jako system rozproszony. WCF rozwiązał niektóre z tych ograniczeń, opracowując i dokumentując zastrzeżone protokoły rozszerzenia dla stosu SOAP, ale kosztem braku obsługi z innych platform.

Windows Communication Foundation jest platformą dla tworzenia usług. Został zaprojektowany na początku 2000 roku, aby pomóc programistom korzystającym z wczesnego SOA do zarządzania złożonością pracy z SOAP. Mimo że usuwa wymóg dla deweloperów do pisania własnych protokołów PROTOKOŁU SOAP, WCF nadal używa protokołu SOAP, aby włączyć współdziałanie z innymi systemami. WCF został również zaprojektowany do dostarczania rozwiązań w wielu protokołach (HTTP/1.1, Net.TCP i tak dalej).

## <a name="microservices"></a>Mikrousługi

W architekturach mikrousług dużych aplikacji są tworzone jako zbiór mniejszych usług modułowych. Każdy składnik wykonuje określone zadanie lub proces, a składniki są przeznaczone do pracy interoperacyjnej, ale mogą być izolowane w razie potrzeby.

Zalety mikrousług obejmują:

- Zmiany i uaktualnienia mogą być obsługiwane niezależnie.
- Obsługa błędów staje się bardziej wydajne, ponieważ problemy mogą być śledzone do określonych usług, które są następnie izolowane, przebudowany, przetestowane i ponownie rozmieszczony niezależnie od innych usług.
- Skalowalność może być ograniczona do określonych wystąpień lub usług, a nie całej aplikacji.
- Programowanie może się zdarzyć w wielu zespołach, z mniejszym tarciem niż występuje, gdy wiele zespołów pracuje nad jedną bazą kodu.

Przejście na zwiększenie wirtualizacji, przetwarzania w chmurze, kontenerów i Internetu rzeczy przyczyniło się do ciągłego wzrostu liczby mikrousług. Ale mikrousługi nie są bez ich wyzwań. Rozdrobniona/zdecentralizowana infrastruktura kładła większy nacisk na potrzebę prostoty i szybkości komunikacji między usługami. To z kolei zwróciło uwagę na czasami pracochłonne i skrzywione charakter SOAP.

To właśnie w tym środowisku gRPC został uruchomiony, 10 lat po tym, jak Microsoft po raz pierwszy wydał WCF. Ewoluował bezpośrednio z wewnętrznej infrastruktury Google RPC (Stubby), gRPC nigdy nie był oparty na tych samych standardach i protokołach, które informowały parametry wielu wcześniejszych kontrolerów RC. A gRPC był tylko kiedykolwiek oparty na HTTP / 2. Dlatego może korzystać z nowych możliwości, które dostarczył zaawansowany protokół transportowy. W szczególności dwukierunkowe przesyłanie strumieniowe, wiadomości binarne i multipleksowanie.

## <a name="about-this-guide"></a>O tym przewodniku

Niniejszy przewodnik obejmuje najważniejsze cechy gRPC. Wczesne rozdziały przyjrzyj się na wysokim poziomie głównym cechom WCF i porównują je z cechami gRPC. Określa ona, gdzie istnieją bezpośrednie korelacje między WCF i gRPC, a także gdzie gRPC oferuje przewagę. Jeśli nie ma korelacji między WCF i gRPC lub gdy gRPC nie jest w stanie zaoferować równoważne rozwiązanie WCF, ten przewodnik zaproponuje obejścia lub gdzie iść, aby uzyskać więcej informacji.

Przy użyciu zestawu przykładowych aplikacji WCF, Rozdział 5 jest dogłębne spojrzenie na konwersję głównych typów usługi WCF (proste żądanie odpowiedzi, jednokierunkowe i przesyłania strumieniowego) do ich odpowiedników w gRPC.

Ostatnia część książki analizuje, jak uzyskać najlepsze z gRPC w praktyce. Ta sekcja zawiera informacje na temat korzystania z dodatkowych narzędzi, takich jak kontenery platformy Docker lub Kubernetes, aby skorzystać z wydajności gRPC. Zawiera również szczegółowe spojrzenie na monitorowanie z rejestrowania, metryki i śledzenia rozproszonego.

## <a name="who-this-guide-is-for"></a>Dla kogo przeznaczony jest ten przewodnik

Ten przewodnik został napisany dla deweloperów pracujących w programie .NET Framework lub .NET Core, którzy korzystali z WCF i którzy chcą przeprowadzić migrację swoich aplikacji do nowoczesnego środowiska RPC dla wersji .NET Core 3.0 i nowszych. Przewodnik może być również przydatne bardziej ogólnie dla deweloperów uaktualnienia lub rozważa uaktualnienie do .NET Core 3.0 i którzy chcą korzystać z wbudowanych narzędzi gRPC.

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[następny](grpc-overview.md)
