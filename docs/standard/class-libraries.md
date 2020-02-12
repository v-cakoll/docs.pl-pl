---
title: Biblioteki klas .NET
description: Dowiedz się, jak biblioteki klas .NET umożliwiają grupowanie przydatnych funkcji w moduły, które mogą być używane przez wiele aplikacji.
author: richlander
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: a67484c3-fe92-44d8-8fa3-36fa2071d880
ms.openlocfilehash: b7934e5def202760ab05d363ee5fcda5d012ca72
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124588"
---
# <a name="net-class-libraries"></a>Biblioteki klas .NET

Biblioteki klas są koncepcją [biblioteki udostępnionej](https://en.wikipedia.org/wiki/Library_%28computing%29#Shared_libraries) dla platformy .NET. Umożliwiają one componentize przydatną funkcjonalność do modułów, które mogą być używane przez wiele aplikacji. Mogą one również służyć jako sposób ładowania funkcjonalności, która nie jest wymagana lub jest nieznana podczas uruchamiania aplikacji. Biblioteki klas są opisane przy użyciu [formatu pliku zestawu platformy .NET](assembly/file-format.md).

Istnieją trzy typy bibliotek klas, których można użyć:

* Biblioteki klas **specyficzne dla platformy** mają dostęp do wszystkich interfejsów API w danej platformie (na przykład .NET Framework, Xamarin iOS), ale mogą być używane tylko przez aplikacje i biblioteki przeznaczone dla tej platformy.
* **Przenośne** biblioteki klas mają dostęp do podzestawu interfejsów API i mogą być używane przez aplikacje i biblioteki przeznaczone dla wielu platform.
* Biblioteki klas **.NET Standard** są fuzją koncepcji biblioteki dla platformy i przenośnej w jeden model, który zapewnia najlepsze z nich.

## <a name="platform-specific-class-libraries"></a>Biblioteki klas specyficzne dla platformy

Biblioteki specyficzne dla platformy są powiązane z pojedynczą implementacją platformy .NET (na przykład .NET Framework w systemie Windows) i w związku z tym mogą przyjmować znaczące zależności w znanym środowisku wykonawczym. Takie środowisko spowoduje udostępnienie znanego zestawu interfejsów API (interfejsów API platformy .NET i systemu operacyjnego) oraz udostępnienie i uwidocznienie oczekiwanego stanu (na przykład rejestru systemu Windows).

Deweloperzy, którzy tworzą biblioteki specyficzne dla platformy, mogą w pełni wykorzystać podstawową platformę. Biblioteki będą kiedykolwiek działać tylko na danej platformie, dzięki czemu testy platformy lub inne formy kodu warunkowego są zbędne (modulo pojedynczy kod pochodzenia dla wielu platform).

Biblioteki specyficzne dla platformy były typu biblioteki klas podstawowych dla .NET Framework. Podobnie jak w przypadku innych implementacji platformy .NET, biblioteki specyficzne dla platformy pozostawały w typie biblioteki dominującej.

## <a name="portable-class-libraries"></a>Przenośne biblioteki klas

Biblioteki przenośne są obsługiwane w wielu implementacjach platformy .NET. Mogą oni nadal przyjmować zależności w znanym środowisku wykonawczym, jednak środowisko jest to syntetyczne, które jest generowane przez część wspólną zestawu konkretnych implementacji platformy .NET. Oznacza to, że uwidocznione interfejsy API i założenia platformy są podzbiorem dostępności dla biblioteki specyficznej dla platformy.

Podczas tworzenia biblioteki przenośnej wybiera się konfigurację platformy. To jest zestaw platform, które muszą być obsługiwane (na przykład .NET Framework 4.5 +, Windows Phone 8.0 +). Im więcej platform można obsłużyć, tym mniej interfejsów API i mniejszych założeń platformy, które można utworzyć, najniższego wspólnego mianownika. Ta cecha może być w pierwszej kolejności myląca, ponieważ ludzie często uważają, że większa jest lepsza

Wielu deweloperów biblioteki przełączyli się od tworzenia wielu bibliotek specyficznych dla platformy z jednego źródła (przy użyciu dyrektyw kompilacji warunkowej) do bibliotek przenośnych. Istnieje [kilka podejścia](https://blog.stephencleary.com/2012/11/portable-class-library-enlightenment.html) do uzyskiwania dostępu do funkcji specyficznych dla platformy w bibliotekach przenośnych, [a](https://log.paulbetts.org/the-bait-and-switch-pcl-trick/) w tym momencie jest to najczęściej zaakceptowana technika.

## <a name="net-standard-class-libraries"></a>.NET Standard biblioteki klas

Biblioteki .NET Standard są zastępowane pojęcia dotyczące bibliotek i elementów przenośnych specyficznych dla platformy. Są one specyficzne dla platformy w tym sensie, że uwidaczniają wszystkie funkcje z poziomu podstawowej platformy (nie zawiera żadnych platform syntetycznych lub przecięć platform). Są one przenośne w tym sensie, że działają na wszystkich platformach pomocniczych.

.NET Standard uwidacznia zestaw _kontraktów_biblioteki. Implementacje platformy .NET muszą obsługiwać wszystkie umowy w całości lub wcale. W związku z tym każda implementacja obsługuje zestaw kontraktów .NET Standard. Współrzuty polega na tym, że każda biblioteka klas .NET Standard jest obsługiwana na platformach, które obsługują jej zależności kontraktu.

.NET Standard nie uwidacznia całej funkcjonalności .NET Framework (nie jest to cel), ale udostępnia wiele innych interfejsów API niż przenośne biblioteki klas. Więcej interfejsów API zostanie dodanych w czasie.

Następujące platformy obsługują biblioteki .NET Standard:

* .NET Core
* .NET Framework
* Mono
* Xamarin.iOS, Xamarin.Mac, Xamarin.Android
* Platforma uniwersalna systemu Windows (UWP)
* System Windows
* Windows Phone
* Windows Phone Silverlight

Aby uzyskać więcej informacji, zobacz temat [.NET Standard](net-standard.md) .

## <a name="mono-class-libraries"></a>Biblioteki klas mono

Biblioteki klas są obsługiwane przez mono, w tym trzy typy bibliotek opisanych powyżej. Język mono jest często widoczny (poprawnie) jako implementacja międzyplatformowa platformy Microsoft .NET. W części jest to spowodowane tym, że biblioteki .NET Framework specyficzne dla platformy mogą działać w środowisku uruchomieniowym mono bez modyfikacji ani ponownej kompilacji. Ta cecha była przed utworzeniem bibliotek klas przenośnych, dlatego była oczywistym wyborem umożliwiającym obsługę binarnej przenośności między .NET Framework i mono (chociaż działa tylko w jednym kierunku).
