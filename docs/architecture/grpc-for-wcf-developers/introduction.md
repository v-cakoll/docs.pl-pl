---
title: Wprowadzenie — gRPC dla deweloperów WCF
description: Wprowadzenie
ms.date: 09/02/2019
ms.openlocfilehash: 3fb7ae440f65cc2daa2a2c984d01d0c0c1eac0aa
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967618"
---
# <a name="introduction"></a>Wprowadzenie

Pomoc dla maszyn komunikujących się ze sobą jest jednym z podstawowych postanowień w wieku cyfrowym. W szczególności istnieje ciągły nakład na określenie optymalnego mechanizmu komunikacji zdalnej, który będzie odpowiadał wymaganiom związanym z współdziałaniem bieżącej infrastruktury. Jak można wyobrazić, ten mechanizm zmienia się w zależności od potrzeb lub infrastruktury.

Wydanie programu .NET Core 3,0 oznacza zmianę sposobu, w jaki firma Microsoft dostarcza rozwiązania komunikacji zdalnej dla deweloperów, którzy chcą dostarczać usługi na różnych platformach. Platforma .NET Core nie oferuje Windows Communication Foundation (WCF) z usługi Box, ale w wersji ASP.NET Core 3,0 zapewnia wbudowaną funkcję gRPC.

gRPC to popularna platforma w szerszej społeczności oprogramowania, używana przez deweloperów w wielu językach programowania dla nowoczesnych scenariuszy RPC. Społeczność i ekosystem są żywe i aktywne, z obsługą protokołu gRPC dodawanego do składników infrastruktury, takich jak Kubernetes, siatki usług, moduły równoważenia obciążenia i nie tylko. Te czynniki, a także jego wydajność, wydajność i zgodność między platformami, umożliwiają gRPC naturalny wybór dla nowych aplikacji i aplikacji WCF przenoszonych na platformę .NET Core.

## <a name="history"></a>Historia

Podstawowa zasada w sieci komputerowej nie większa niż grupa komputerów wymieniających dane ze sobą w celu osiągnięcia zestawu powiązanych zadań, które nie uległy zmianie od momentu jego powstania. Jednak stopień złożoności, skali i oczekiwania jest wykładniczy.  

W 1990s wyróżnienie dotyczyło głównie ulepszania sieci wewnętrznych przy użyciu tego samego języka i platform. Protokół TCP/IP stał się standardem Gold dla tego typu komunikacji.

Jednak fokus jest wkrótce przenoszony do optymalnej optymalizacji komunikacji na wielu platformach promującej podejście niezależny od języka. Architektura zorientowana na usługę (SOA) udostępnia strukturę swobodnego sprzęgania szerokiej kolekcji usług, które mogą być udostępniane aplikacji.

Opracowywanie *usług sieci Web* ma miejsce, gdy wszystkie główne platformy mogą uzyskać dostęp do Internetu, ale nadal nie mogą ze sobą współistnieć. Usługi sieci Web mają otwarte standardy i protokoły, w tym:

- XML do tagów i danych kodu;
- Simple Object Access Protocol (SOAP) do transferowania danych;
- Web Services Definition Language (WSDL) — opisuje i nawiązuje połączenie usługi sieci Web z aplikacją kliencką. *i*
- Integracja z odnajdywaniem uniwersalnym (UDDI) — umożliwia odnajdywanie usług sieci Web przy użyciu innych usług.

Protokół SOAP definiuje reguły, za pomocą których elementy rozproszone aplikacji mogą komunikować się ze sobą, nawet jeśli znajdują się na różnych platformach. Protokół SOAP jest oparty na kodzie XML, więc jest czytelny dla użytkownika. W celu łatwego zrozumienia protokołu SOAP jest to rozmiar. Komunikaty protokołu SOAP są większe niż komunikaty w porównywalnych protokołach. Protokół SOAP został zaprojektowany, aby podzielić aplikacje monolityczne na formularz wieloskładnikowy bez utraty zabezpieczeń lub kontroli. W związku z tym program WCF został zaprojektowany do pracy z tym rodzajem systemu, w przeciwieństwie do gRPC, który rozpoczął się jako system rozproszony. Usługa WCF dotyczyła niektórych z tych ograniczeń przez opracowywanie i dokumentowanie własnych protokołów rozszerzeń dla stosu protokołu SOAP, ale kosztem niewsparcia z innych platform.

Windows Communication Foundation to struktura do kompilowania usług. Została zaprojektowana na wczesnych wersjach 2000, aby ułatwić deweloperom korzystanie z wczesnego SOA do zarządzania złożonością pracy z protokołem SOAP. Mimo że eliminuje wymóg tworzenia własnych protokołów SOAP przez dewelopera, usługa WCF nadal używa protokołu SOAP do zapewnienia współdziałania z innymi systemami. Program WCF został również zaprojektowany w celu dostarczania rozwiązań między wieloma protokołami (HTTP/1.1, NetTCP itd.).

## <a name="microservices"></a>Mikrousługi

W przypadku architektur mikrousług duże aplikacje są kompilowane jako kolekcja mniejszych usług modułowych. Każdy składnik wykonuje określone zadanie lub proces, a składniki są przeznaczone do pracy, ale mogą być odizolowane w razie potrzeby.

Zalety mikrousług obejmują:

- Zmiany i uaktualnienia mogą być obsługiwane niezależnie.
- Obsługa błędów stanie się bardziej wydajna, ponieważ problemy mogą być śledzone dla konkretnych usług, które są następnie odizolowane, odtworzone, przetestowane i ponownie wdrożone niezależnie od innych usług.
- Skalowalność może być ograniczona do określonych wystąpień lub usług, a nie całej aplikacji.
- Programowanie może odbywać się w wielu zespołach, z mniejszą ilością problemów, gdy wiele zespołów pracuje w pojedynczej bazie kodu.

Przejście do coraz większej wirtualizacji, przetwarzania danych w chmurze, kontenerów i Internet rzeczyów przyczyniło się do ciągłego wzrostu mikrousług. Jednak mikrousługi nie mają żadnych wyzwań. W przypadku infrastruktury pofragmentowanej/zdecentralizowanej coraz częściej zachodzi potrzeba uproszczenia i przyspieszenia komunikacji między usługami. To z kolei nastąpiło zwrócenie uwagi do czasami pracochłonne i nieskażony charakter protokołu SOAP.

Była w tym środowisku, że gRPC został uruchomiony, 10 lat po pierwszym wydaniu WCF przez firmę Microsoft. W przypadku rozwijającego się bezpośrednio z usługi RPC infrastruktury wewnętrznej firmy Google (stubby), gRPC nigdy nie opierał się na tych samych standardach i protokołach, które powiadomiły parametry wielu wcześniejszych wywołań RPC. Ponadto gRPC była kiedykolwiek oparta na protokole HTTP/2 i dlatego może nastąpić w przypadku nowych funkcji oferowanych przez zaawansowany protokół transportowy. W szczególności dwukierunkowe przesyłanie strumieniowe, obsługa komunikatów binarnych i multipleksowanie.

## <a name="about-this-guide"></a>O tym przewodniku

Ten przewodnik obejmuje najważniejsze funkcje gRPC. Wczesne rozdziały mają ogólny wygląd głównych funkcji programu WCF i porównaj je z gRPC. Określa, gdzie są bezpośrednie korelacje między WCF i gRPC, a także miejsce, w którym gRPC oferuje zalety. W przypadku braku korelacji między usługą WCF i gRPC lub gRPC nie jest możliwe zaoferowanie równoważnego rozwiązania WCF, w tym przewodniku opisano obejścia lub miejsca, w których można znaleźć więcej informacji.

Korzystając z zestawu przykładowych aplikacji WCF, rozdział 5 to głębokie szczegółowee wyszukiwanie w celu przeprowadzenia konwersji głównych typów usług WCF (prosta odpowiedź na żądanie, jednokierunkowe i przesyłania strumieniowego) do ich odpowiedników w gRPC.

W ostatniej sekcji książki zawarto informacje na temat najlepszego gRPC w pracy, w tym przy użyciu dodatkowych narzędzi, takich jak kontenery Docker lub Kubernetes, aby wykorzystać wydajność usługi gRPC oraz szczegółowy opis monitorowania z rejestrowaniem, metrykami i dystrybuowaniem pochodzenia.

## <a name="whom-this-guide-is-for"></a>Którego dotyczy ten przewodnik

Ten przewodnik został utworzony dla deweloperów pracujących w .NET Framework lub .NET Core, którzy wcześniej korzystali z usług WCF i chcący migrować swoje aplikacje do nowoczesnego środowiska RPC dla programu .NET Core 3,0 i jego nowszych wersji. Przewodnik może być również bardziej używany w przypadku deweloperów uaktualniających lub rozważających uaktualnienie do programu .NET Core 3,0, którzy chcą korzystać z wbudowanych narzędzi gRPC.

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[Następny](grpc-overview.md)
