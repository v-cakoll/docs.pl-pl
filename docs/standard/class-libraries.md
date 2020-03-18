---
title: Biblioteki klas .NET
description: Dowiedz się, jak biblioteki klas .NET umożliwiają grupowanie użytecznych funkcji w moduły, które mogą być używane przez wiele aplikacji.
author: richlander
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: a67484c3-fe92-44d8-8fa3-36fa2071d880
ms.openlocfilehash: b7934e5def202760ab05d363ee5fcda5d012ca72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77124588"
---
# <a name="net-class-libraries"></a>Biblioteki klas .NET

Biblioteki klas są koncepcją [biblioteki udostępnionej](https://en.wikipedia.org/wiki/Library_%28computing%29#Shared_libraries) dla .NET. Umożliwiają one zestawienie przydatnych funkcji w moduły, które mogą być używane przez wiele aplikacji. Mogą być również używane jako sposób ładowania funkcji, które nie są potrzebne lub nie są znane podczas uruchamiania aplikacji. Biblioteki klas są opisane przy użyciu [formatu pliku .NET Assembly](assembly/file-format.md).

Istnieją trzy typy bibliotek klas, których można użyć:

* Biblioteki klas **specyficzne dla platformy** mają dostęp do wszystkich interfejsów API na danej platformie (na przykład .NET Framework, Xamarin iOS), ale mogą być używane tylko przez aplikacje i biblioteki, które są przeznaczone dla tej platformy.
* **Przenośne** biblioteki klas mają dostęp do podzbioru interfejsów API i mogą być używane przez aplikacje i biblioteki przeznaczone na wiele platform.
* Biblioteki klas **.NET Standard** są połączeniem koncepcji biblioteki specyficznej dla platformy i przenośnej w jeden model, który zapewnia najlepsze z obu.

## <a name="platform-specific-class-libraries"></a>Biblioteki klas specyficzne dla platformy

Biblioteki specyficzne dla platformy są powiązane z pojedynczą implementacją .NET (na przykład .NET Framework w systemie Windows) i w związku z tym mogą mieć znaczące zależności od znanego środowiska wykonywania. Takie środowisko uwidacznia znany zestaw interfejsów API (.NET i OS API) i będzie utrzymywać i udostępniać oczekiwany stan (na przykład rejestr systemu Windows).

Deweloperzy, którzy tworzą biblioteki specyficzne dla platformy można w pełni wykorzystać platformę podstawową. Biblioteki będą działać tylko na danej platformie, dzięki czemu sprawdza niepotrzebna lub inne formy kodu warunkowego (kod pojedynczego źródła modulo dla wielu platform).

Biblioteki specyficzne dla platformy zostały typu biblioteki klasy podstawowej dla .NET Framework. Nawet w miarę pojawiania się innych implementacji .NET biblioteki specyficzne dla platformy pozostały dominującym typem biblioteki.

## <a name="portable-class-libraries"></a>Przenośne biblioteki klas

Biblioteki przenośne są obsługiwane w wielu implementacjach .NET. Nadal mogą przyjmować zależności od znanego środowiska wykonywania, jednak środowisko jest syntetyczne, które jest generowane przez przecięcie zestawu konkretnych implementacji .NET. Oznacza to, że udostępniane interfejsy API i założenia platformy są podzbiorem tego, co będzie dostępne dla biblioteki specyficznej dla platformy.

Podczas tworzenia przenośnej biblioteki można wybrać konfigurację platformy. Są to zestaw platform, które należy obsługiwać (na przykład .NET Framework 4.5+, Windows Phone 8.0+). Im więcej platform zdecydujesz się obsługiwać, tym mniej interfejsów API i mniej założeń platformy można zrobić, najniższy wspólny mianownik. Ta cecha może być mylące na początku, ponieważ ludzie często myślą "więcej jest lepiej", ale okaże się, że więcej obsługiwanych platform powoduje mniej dostępnych interfejsów API.

Wielu deweloperów biblioteki przestawiło się z tworzenia wielu bibliotek specyficznych dla platformy z jednego źródła (przy użyciu dyrektyw kompilacji warunkowej) do bibliotek przenośnych. Istnieje [kilka metod](https://blog.stephencleary.com/2012/11/portable-class-library-enlightenment.html) uzyskiwania dostępu do funkcji specyficznych dla platformy w bibliotekach przenośnych, z [przynętą i przełącznikiem](https://log.paulbetts.org/the-bait-and-switch-pcl-trick/) jest najczęściej akceptowaną techniką w tym momencie.

## <a name="net-standard-class-libraries"></a>Biblioteki klas .NET Standard

Biblioteki .NET Standard zastępują pojęcia dotyczące bibliotek specyficznych dla platformy i przenośnych. Są one specyficzne dla platformy w tym sensie, że ujawniają wszystkie funkcje z platformy bazowej (brak syntetycznych platform lub przecięć platformy). Są przenośne w tym sensie, że działają na wszystkich platformach pomocniczych.

Standard .NET udostępnia zestaw _kontraktów_biblioteki . Implementacje .NET muszą obsługiwać każdą umowę w pełni lub wcale. Każda implementacja obsługuje zatem zestaw kontraktów .NET Standard. W powiastów jest, że każda biblioteka klas .NET Standard jest obsługiwana na platformach, które obsługują jego zależności kontraktu.

Standard .NET nie udostępnia całej funkcjonalności programu .NET Framework (ani nie jest to cel), jednak nie uwidaczniają wiele więcej interfejsów API niż przenośne biblioteki klas. Więcej interfejsów API zostaną dodane w czasie.

Następujące platformy obsługują biblioteki .NET Standard:

* .NET Core
* .NET Framework
* Mono
* Xamarin.iOS, Xamarin.Mac, Xamarin.Android
* Platforma uniwersalna systemu Windows (UWP)
* Windows
* Windows Phone
* Windows Phone Silverlight

Aby uzyskać więcej informacji, zobacz temat [.NET Standard.](net-standard.md)

## <a name="mono-class-libraries"></a>Biblioteki klas mono

Biblioteki klas są obsługiwane w mono, w tym trzy typy bibliotek opisanych powyżej. Mono jest często postrzegany (poprawnie) jako implementacja między platformami programu Microsoft .NET Framework. Po części było to spowodowane platformy specyficzne .NET Framework biblioteki można uruchomić w czasie wykonywania Mono bez modyfikacji lub ponownej kompilacji. Ta cecha została w miejscu przed utworzeniem przenośnych bibliotek klas, więc był oczywistym wyborem, aby umożliwić przenośność binarną między .NET Framework i Mono (chociaż działał tylko w jednym kierunku).
