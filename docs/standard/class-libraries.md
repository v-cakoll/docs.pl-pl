---
title: Biblioteki klas .NET
description: "Dowiedz się, jak bibliotek klas .NET umożliwia przydatne funkcje grupy do modułów, które mogą być używane przez wiele aplikacji."
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: a67484c3-fe92-44d8-8fa3-36fa2071d880
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8f7c421d2490678f7122e78bc0b83ebf3a1aa9ea
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="net-class-libraries"></a>Biblioteki klas .NET

Biblioteki klas są [biblioteki udostępnionej](http://en.wikipedia.org/wiki/Library_%28computing%29#Shared_libraries) pojęcia dla platformy .NET. Umożliwiają one componentize przydatne funkcje do modułów, które mogą być używane przez wiele aplikacji. One mogą służyć jako środek ładowania funkcji nie jest wymagane lub nieznany podczas uruchamiania aplikacji. Biblioteki klas są opisane przy użyciu [format pliku zestawu .NET](assembly-format.md).

Istnieją trzy typy bibliotek klas, które są dostępne:

*   **Specyficzne dla platformy** bibliotek klas mają dostęp do wszystkich interfejsów API w danej platformy (na przykład, .NET Framework Xamarin iOS), ale może być używany tylko przez aplikacji i bibliotek przeznaczonych do danej platformy.
*   **Przenośne** bibliotek klas mają dostęp do podzestawu interfejsów API i mogą być używane przez aplikacje i bibliotek przeznaczonych dla wielu platform.
*   **.NET standard** bibliotek klas są połączenia koncepcji specyficzne dla platformy, przenośne biblioteki do pojedynczego modelu, który zapewnia najlepsze cechy obu.

## <a name="platform-specific-class-libraries"></a>Biblioteki klas specyficzne dla platformy

Biblioteki specyficzne dla platformy są powiązane z pojedynczą implementacją .NET (na przykład, .NET Framework w systemie Windows) i w związku z tym może zająć znaczących zależności w środowisku wykonywania znane. Takim środowisku będzie ujawnia znanego zestawu interfejsów API (.NET i interfejsów API systemu operacyjnego) i będzie Obsługa i ujawnia oczekiwanym stanem (na przykład rejestru systemu Windows).

Deweloperzy tworzący biblioteki określonej platformy można w pełni wykorzystać możliwości platformy. Biblioteki tylko będzie działać w podanej platformy wprowadzania kontrole platformy lub inne formy warunkowego kodu niepotrzebnych (modulo pojedynczego źródeł kodu dla wielu platform).

Specyficzne dla platformy biblioteki zostały typu klasy podstawowej biblioteki platformy .NET Framework. Również w innych implementacjach .NET przywołane, specyficzne dla platformy bibliotek pozostały typu dominującą biblioteki.

## <a name="portable-class-libraries"></a>Biblioteki klas przenośnych

Przenośnej biblioteki są obsługiwane na wiele implementacji .NET. Nadal może zająć zależności w środowisku wykonywania znane, jednak środowisko jest syntetycznych jedną, która jest generowana przez przecięcie zestaw konkretnych implementacje .NET. Oznacza to, że narażonych założenia interfejsów API i platforma są podzbiorem jakie byłyby dostępne w bibliotece specyficzne dla platformy.

Konfiguracja platformy można wybrać podczas tworzenia biblioteki przenośnej. Są to zbiór platformy, które są potrzebne do obsługi (na przykład, .NET Framework 4.5 +, Windows Phone 8.0 i nowsze). Więcej platformy, z którymi zdecydować się na pomocy technicznej, mniej interfejsów API i mniej założenia platform istnieje możliwość, liczby całkowite. Tej właściwości może być początkowo mylące, od użytkowników często reakcji "więcej lepiej jest", ale Znajdź więcej obsługiwane platformy wyniki w mniejszą liczbę dostępnych interfejsach API.

Wielu deweloperów biblioteki przełączono z produkujących wiele bibliotek specyficzne dla platformy z jednego źródła (przy użyciu dyrektywy warunkowej kompilacji) do bibliotek przenośnych. Istnieją [kilka metod](http://blog.stephencleary.com/2012/11/portable-class-library-enlightenment.html) do uzyskiwania dostępu do funkcji specyficzne dla platformy w przenośnych bibliotekach z [przynęta przełącznika](http://log.paulbetts.org/the-bait-and-switch-pcl-trick/) najbardziej akceptowanego technika w tym momencie.

### <a name="net-standard-class-libraries"></a>Biblioteki standardowe klas .NET

Biblioteki .NET standard to zastąpienie pojęcia biblioteki specyficzne dla platformy i przenośnych. Są one specyficzne dla platformy w tym sensie, że udostępniają wszystkie funkcje z podstawowej platformy (nie syntetycznych platformy lub przecięcia platformy). Są one przenośne w tym sensie, że działają na wszystkich platformach pomocniczych.

.NET Standard udostępnia zestaw biblioteki _kontrakty_. Implementacje .NET musi obsługiwać każdej umowy w całości lub w ogóle. Każda implementacja, w związku z tym obsługuje zestaw kontraktów .NET Standard. Jest następstwem czy każdego .NET Standard biblioteki klas jest obsługiwana na platformach, które obsługują tę jego zależności kontraktu.

.NET Standard nie ujawnia funkcji całego programu .NET Framework (nie jest to, że cel), jednak udostępniają wiele API więcej niż przenośnej biblioteki klas. Interfejsy API więcej zostanie dodany wraz z upływem czasu.

Następujące platformy obsługuje bibliotek .NET Standard:

* .NET Core
* .NET Framework
* Mono
* Xamarin.iOS, Xamarin.Mac, Xamarin.Android
* Platforma uniwersalna systemu Windows (UWP)
* Windows
* Windows Phone
* Windows Phone Silverlight

Aby uzyskać więcej informacji, zobacz [.NET Standard](net-standard.md) tematu.

### <a name="mono-class-libraries"></a>Biblioteki klas mono

Biblioteki klas są obsługiwane w Mono, w tym trzy rodzaje bibliotek opisane powyżej. Mono często zaobserwowano (poprawnie) jako implementację i platform, programu Microsoft .NET Framework. W części działo się tak dlatego specyficzne dla platformy .NET Framework biblioteki można uruchomić na Mono środowiska uruchomieniowego bez modyfikacji lub ponownej kompilacji. Ta cecha był zainstalowany przed tworzeniem bibliotek klas przenośnych została tak oczywiste wyboru umożliwiające binarne przenoszenia między .NET Framework i Mono (mimo że tylko działał w jednym kierunku).
