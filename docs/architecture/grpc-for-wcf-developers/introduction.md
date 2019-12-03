---
title: Wprowadzenie — gRPC dla deweloperów WCF
description: Wprowadzenie
ms.date: 09/02/2019
ms.openlocfilehash: 2f36d6294e2c76309b051fb3af21157cbfc1087a
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711233"
---
# <a name="introduction"></a>Wprowadzenie

Pomoc dla maszyn komunikujących się ze sobą jest jednym z podstawowych postanowień w wieku cyfrowym. W szczególności istnieje ciągły nakład na określenie optymalnego mechanizmu komunikacji zdalnej, który będzie odpowiadał wymaganiom związanym z współdziałaniem bieżącej infrastruktury. Jak można wyobrazić, ten mechanizm zmienia się w zależności od potrzeb lub infrastruktury.

Wydanie programu .NET Core 3,0 oznacza zmianę sposobu, w jaki firma Microsoft dostarcza rozwiązania komunikacji zdalnej dla deweloperów, którzy chcą dostarczać usługi na różnych platformach. Platforma .NET Core nie oferuje Windows Communication Foundation (WCF) z usługi Box, ale z wersją ASP.NET Core 3,0 zapewnia wbudowaną funkcję gRPC.

gRPC to popularna platforma w szerszej społeczności oprogramowania. Są one używane przez deweloperów w wielu językach programowania dla nowoczesnych scenariuszy RPC. Społeczność i ekosystem są żywe i aktywne. Obsługa protokołu gRPC jest dodawana do składników infrastruktury, takich jak Kubernetes, siatki usług, moduły równoważenia obciążenia i nie tylko. Te czynniki wraz z wydajnością, efektywnością i międzyplatformową zgodnością gRPCą naturalny wybór dla nowych aplikacji i aplikacji WCF przenoszonych do platformy .NET Core.

## <a name="history"></a>Historia

Podstawowa zasada w sieci komputerowej nie większa niż grupa komputerów wymieniających dane ze sobą w celu osiągnięcia zestawu powiązanych zadań, które nie uległy zmianie od momentu jego powstania. Jednak stopień złożoności, skali i oczekiwań był wykładniczy.  

W 1990s wyróżnienie dotyczyło głównie ulepszania sieci wewnętrznych korzystających z tego samego języka i platform. Protokół TCP/IP stał się standardem Gold dla tego typu komunikacji.

Fokus jest wkrótce przenoszony do optymalnej optymalizacji komunikacji na wielu platformach przez promowanie podejścia niezależny odego w języku. Architektura zorientowana na usługę (SOA) udostępnia strukturę swobodnego sprzęgania szerokiej kolekcji usług, które mogą być udostępniane aplikacji.

Opracowywanie *usług sieci Web* ma miejsce, gdy wszystkie główne platformy mogą uzyskać dostęp do Internetu, ale nadal nie mogą ze sobą współistnieć. Usługi sieci Web mają otwarte standardy i protokoły, w tym:

- Kod XML do oznaczania i kodowania danych.
- Simple Object Access Protocol (SOAP) do transferowania danych.
- Język definicji usług sieci Web (WSDL) do opisywania i łączenia usług sieci Web z aplikacjami klienckimi.
- Universal Description, Discovery, and Integration (UDDI), aby usługi sieci Web mogły być odnajdywane przez inne usługi.

Protokół SOAP definiuje reguły, za pomocą których elementy rozproszone aplikacji mogą komunikować się ze sobą, nawet jeśli znajdują się na różnych platformach. Protokół SOAP jest oparty na kodzie XML, więc jest czytelny dla użytkownika. W celu łatwego zrozumienia protokołu SOAP jest to rozmiar. Komunikaty protokołu SOAP są większe niż komunikaty w porównywalnych protokołach. Protokół SOAP został zaprojektowany tak, aby zerwać aplikacje monolityczne w formie wieloskładnikowej bez utraty zabezpieczeń lub kontroli. Dlatego platforma WCF została zaprojektowana tak, aby działała z tym rodzajem systemu, w przeciwieństwie do gRPC, który rozpoczął się jako system rozproszony. Usługa WCF dotyczyła niektórych z tych ograniczeń przez opracowywanie i dokumentowanie własnych protokołów rozszerzeń dla stosu protokołu SOAP, ale kosztem braku pomocy technicznej z innych platform.

Windows Communication Foundation to struktura do kompilowania usług. Została zaprojektowana na wczesnych wersjach 2000, aby ułatwić deweloperom korzystanie z wczesnego SOA do zarządzania złożonością pracy z protokołem SOAP. Chociaż eliminuje to wymaganie, aby deweloperzy mogli pisać własne protokoły protokołu SOAP, usługa WCF nadal używa protokołu SOAP do zapewnienia współdziałania z innymi systemami. Program WCF został również zaprojektowany w celu dostarczania rozwiązań między wieloma protokołami (HTTP/1.1, net. TCP itd.).

## <a name="microservices"></a>Mikrousług

W przypadku architektur mikrousług duże aplikacje są kompilowane jako kolekcja mniejszych usług modułowych. Każdy składnik wykonuje określone zadanie lub proces, a składniki są przeznaczone do pracy, ale mogą być odizolowane w razie potrzeby.

Zalety mikrousług obejmują:

- Zmiany i uaktualnienia mogą być obsługiwane niezależnie.
- Obsługa błędów jest wydajniejsza, ponieważ problemy mogą być śledzone dla konkretnych usług, które są następnie odizolowane, ponownie skompilowane, przetestowane i ponownie wdrożone niezależnie od innych usług.
- Skalowalność może być ograniczona do określonych wystąpień lub usług, a nie całej aplikacji.
- Programowanie może odbywać się w wielu zespołach, z mniejszą ilością problemów, gdy wiele zespołów pracuje w pojedynczej bazie kodu.

Przejście do coraz większej wirtualizacji, przetwarzania danych w chmurze, kontenerów i Internet rzeczyu przyczynia się do ciągłego wzrostu mikrousług. Ale mikrousługi nie mają swoich wyzwań. Pofragmentowana/Zdecentralizowana infrastruktura ma coraz większy nacisk na konieczność uproszczenia i przyspieszenia komunikacji między usługami. To z kolei nastąpiło zwrócenie uwagi do czasami pracochłonne i nieskażony charakter protokołu SOAP.

Była w tym środowisku, że gRPC został uruchomiony, 10 lat po pierwszym wydaniu WCF przez firmę Microsoft. W przypadku rozwijającego się bezpośrednio z usługi RPC infrastruktury wewnętrznej firmy Google (stubby), gRPC nigdy nie opierał się na tych samych standardach i protokołach, które powiadomiły parametry wielu wcześniejszych wywołań RPC. I gRPC była kiedykolwiek oparta na protokole HTTP/2. To dlatego, że może narysować nowe funkcje, które zapewnia zaawansowany protokół transportowy. W szczególności dwukierunkowe przesyłanie strumieniowe, obsługa komunikatów binarnych i multipleksowanie.

## <a name="about-this-guide"></a>O tym przewodniku

Ten przewodnik obejmuje najważniejsze funkcje gRPC. Wczesne rozdziały mają ogólny wygląd głównych funkcji programu WCF i porównują je z tymi gRPCami. Określa, gdzie istnieją bezpośrednie korelacje między WCF i gRPC, a także miejsce, w którym gRPC oferuje zalety. Gdy nie ma korelacji między usługą WCF i gRPC lub gdy gRPC nie jest w stanie zaoferować równoważne rozwiązanie dla WCF, ten przewodnik zasugeruje obejście lub miejsce, w którym można znaleźć więcej informacji.

Korzystając z zestawu przykładowych aplikacji WCF, rozdział 5 to głębokie szczegółowee, które umożliwiają konwertowanie głównych typów usługi WCF (prosta odpowiedź na żądanie, jednokierunkowe i przesyłanie strumieniowe) do ich odpowiedników w gRPC.

Ostatnia sekcja książki wygląda na to, jak najlepiej uzyskać najlepszą z gRPC. Ta sekcja zawiera informacje o korzystaniu z dodatkowych narzędzi, takich jak kontenery Docker lub Kubernetes, w celu wykorzystania wydajności gRPC. Zawiera również szczegółowy opis monitorowania z rejestrowaniem, metrykami i śledzeniem rozproszonym.

## <a name="who-this-guide-is-for"></a>Dla kogo jest ten przewodnik

Ten przewodnik został utworzony dla deweloperów pracujących w .NET Framework lub .NET Core, którzy korzystali z usług WCF i chcący migrować swoje aplikacje do nowoczesnego środowiska RPC dla programu .NET Core 3,0 i jego nowszych wersji. Przewodnik może być również bardziej przydatny dla deweloperów uaktualniających lub rozważających uaktualnienie do programu .NET Core 3,0 i którzy chcą korzystać z wbudowanych narzędzi gRPC.

>[!div class="step-by-step"]
>[Poprzednie](index.md)
>[dalej](grpc-overview.md)
