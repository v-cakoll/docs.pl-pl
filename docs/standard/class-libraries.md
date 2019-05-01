---
title: Biblioteki klas platformy .NET
description: Dowiedz się, jak biblioteki klas platformy .NET umożliwiają grupy przydatnych funkcji do modułów, które mogą być używane przez wiele aplikacji.
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: a67484c3-fe92-44d8-8fa3-36fa2071d880
ms.openlocfilehash: d5b067f299d96b687d44b83e431d89667f2d84f8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772648"
---
# <a name="net-class-libraries"></a>Biblioteki klas platformy .NET

Biblioteki klas są [biblioteki udostępnionej](https://en.wikipedia.org/wiki/Library_%28computing%29#Shared_libraries) pojęcia dla platformy .NET. Umożliwiają one componentize przydatnych funkcji do modułów, które mogą być używane przez wiele aplikacji. One może również jako sposób ładowania funkcji, nie jest wymagane lub nie jest znany przy uruchamianiu aplikacji. Biblioteki klas są opisane za pomocą [format pliku zestawu .NET](assembly/file-format.md).

Istnieją trzy typy biblioteki klas, które są dostępne:

* **Specyficzne dla platformy** bibliotek klas mają dostęp do wszystkich interfejsów API w danej platformy (na przykład, .NET Framework, Xamarin iOS), ale można używać tylko przy użyciu aplikacji i bibliotek przeznaczonych do danej platformy.
* **Przenośne** biblioteki klas, mają dostęp do podzestawu interfejsów API i mogą być używane przez aplikacje i bibliotek przeznaczonych do wielu platform.
* **.NET standard** bibliotek klas jest łączenie koncepcji specyficzne dla platformy, przenośne biblioteki w jednym modelu, który zapewnia najlepsze cechy obu.

## <a name="platform-specific-class-libraries"></a>Biblioteki klas specyficznych dla platformy

Biblioteki specyficzne dla platformy są powiązane z pojedynczej implementacji .NET (na przykład program .NET Framework na Windows) i w związku z tym może potrwać znaczące zależności od środowiska wykonywania znane. Takie środowisko będzie ujawniać znanego zestawu interfejsów API (.NET i interfejsów API systemu operacyjnego) i będzie utrzymują i udostępnić oczekiwany stan (na przykład Rejestr Windows).

Deweloperzy, którzy tworzą biblioteki określonej platformy można w pełni wykorzystać możliwości platformy. Biblioteki tylko nigdy nie będzie działać na daną platform, co kontrole platformy lub inne formy kod warunkowy niepotrzebne (modulo pojedynczego określania źródła kodu dla wielu platform).

Biblioteki charakterystyczne dla platform zostały klasy podstawowej typu biblioteki dla programu .NET Framework. Nawet przy wzroście powstało inne implementacje platformy .NET, biblioteki charakterystyczne dla platformy pozostały Typ dominujący biblioteki.

## <a name="portable-class-libraries"></a>Biblioteki klas przenośnych

Przenośne biblioteki są obsługiwane przez wiele implementacji .NET. Nadal wejściem w zależności od środowiska wykonywania znanych, jednak środowiska syntetycznych jednego, który jest generowany przez przecięcie zestaw konkretnych implementacji .NET. Oznacza to, czy narażonych założenia platforma i interfejsy API stanowią podzestaw jaki byłyby dostępne dla biblioteki specyficzne dla platformy.

Możesz wybrać konfigurację platformy, po utworzeniu przenośnej biblioteki. Są to zestawu Platform, które są potrzebne do obsługi (na przykład, .NET Framework 4.5 +, Windows Phone 8.0 i nowsze). Więcej platform, które postanowisz pomocy technicznej, mniej interfejsów API i mniej założenia platformy można wprowadzić, liczby całkowite. Cecha ta może być początkowo mylące, od osób, które często reakcji "bardziej lepiej jest", ale Znajdź liczby obsługiwanych platform wyniki w mniejszą liczbę dostępnych interfejsów API.

Wielu programistów biblioteki zostały przełączone z produkcji wiele bibliotek specyficzne dla platformy z jednego źródła (przy użyciu dyrektywy kompilacji warunkowej) bibliotek przenośnych. Istnieją [kilka metod](https://blog.stephencleary.com/2012/11/portable-class-library-enlightenment.html) do uzyskiwania dostępu do funkcji specyficznych dla platformy w obrębie bibliotek przenośnych za pomocą [przynęta i przełącznika](https://log.paulbetts.org/the-bait-and-switch-pcl-trick/) najczęściej akceptowanego technika w tym momencie.

## <a name="net-standard-class-libraries"></a>Biblioteki klas .NET standard

Biblioteki .NET standard to zastąpienie pojęć specyficznych dla platformy i przenośnej biblioteki. Są one specyficzne dla platformy w tym sensie, że udostępniają wszystkie funkcje z podstawowej platformy (nie syntetycznych platformy lub platform przecięcia). Są one przenośne w tym sensie, że działają na wszystkich platformach pomocniczych.

Ujawnia zestaw biblioteki .NET Standard _umów_. Implementacje platformy .NET musi obsługiwać każdej umowy w całości lub w ogóle nie. Każda implementacja w związku z tym, obsługuje zestaw .NET Standard zamówień. Następstwem to, że każdy biblioteki klas .NET Standard jest obsługiwany na platformach, które obsługują zależnościami kontraktu.

.NET Standard nie ujawnia całą funkcjonalność programu .NET Framework (nie jest to, że celem), jednak udostępnić wiele interfejsów API z więcej niż biblioteki klas przenośnych. Więcej interfejsów API zostanie dodany wraz z upływem czasu.

Następujące platformy obsługują biblioteki .NET Standard:

* .NET Core
* .NET Framework
* Mono
* Xamarin.iOS, Xamarin.Mac, Xamarin.Android
* Platforma uniwersalna systemu Windows (UWP)
* Windows
* Windows Phone
* Windows Phone Silverlight

Aby uzyskać więcej informacji, zobacz [.NET Standard](net-standard.md) tematu.

## <a name="mono-class-libraries"></a>Biblioteki klas platformy mono

Biblioteki klas są obsługiwane w Mono, w tym trzy rodzaje bibliotek opisanych powyżej. Narzędzie mono często został napotkany (poprawnie) jako implementacji dla wielu platform, programu Microsoft .NET Framework. W części taka konfiguracja była ponieważ specyficzne dla platformy .NET Framework bibliotek można uruchomić od środowiska uruchomieniowego Mono bez modyfikacji lub ponownej kompilacji. Cecha ta był zainstalowany przed tworzeniem bibliotek klas przenośnych, dlatego został oczywistym wyborem, aby włączyć możliwości binarnego przenoszenia między .NET Framework oraz Mono (chociaż poszło w jednym kierunku).
