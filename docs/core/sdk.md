---
title: "Omówienie zestawu SDK .NET core"
description: "Dowiedz się o .NET Core SDK, czyli zestawowi bibliotek i narzędzi służących do tworzenia projektów .NET Core."
keywords: .NET, .NET core
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 26bc9822-e42b-48ec-b0d6-499dc604add7
ms.workload: dotnetcore
ms.openlocfilehash: f32f4c50f5b3fef8f38560ea3516265f7a4ac008
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="net-core-sdk-overview"></a>Omówienie zestawu SDK .NET core 

## <a name="introduction"></a>Wprowadzenie
.NET core Software Development Kit (SDK) to zestaw bibliotek i narzędzia, które umożliwiają deweloperom tworzenie aplikacji platformy .NET Core i bibliotek. To jest pakiet, który najprawdopodobniej uzyska dostęp do deweloperów. 

Ten przewodnik zawiera następujące składniki:

1. Podstawowe narzędzia wiersza polecenia .NET są używane do tworzenia aplikacji
2. Oprogramowanie .NET core (bibliotek i środowiska uruchomieniowego), które umożliwiają aplikacjom zarówno być zbudowany i uruchom
3. `dotnet` Sterownik do uruchomienia [polecenia interfejsu wiersza polecenia](tools/index.md) oraz uruchamiania aplikacji


## <a name="acquiring-the-net-core-sdk"></a>Uzyskiwanie .NET Core SDK
Podobnie jak w przypadku dowolnego narzędzia, najpierw jest aby uzyskać narzędzia do komputera. W zależności od scenariusza możesz użyć natywnych instalatorów Instalacja zestawu SDK lub użyć skryptu powłoki instalacji.

Natywny instalatorów głównie są przeznaczone dla dewelopera maszyny. Zestaw SDK jest dystrybuowane przy użyciu mechanizmu instalacji natywnych każdej z obsługiwanych platform, na przykład DEB pakietów na funkcji MSI lub Ubuntu pakietów w systemie Windows. Te pliki instalacyjne będzie zainstalować i skonfigurować środowisko, zgodnie z potrzebami dla użytkownika korzystanie z zestawu SDK natychmiast po zakończeniu instalacji. Jednak również potrzebują uprawnień administracyjnych na komputerze. Instrukcje instalacji można wyświetlić w [Przewodnik instalacji platformy .NET Core](https://aka.ms/dotnetcoregs).

Instalowanie skryptów, z drugiej strony, nie wymaga uprawnień administracyjnych. Jednak one również nie zostaną zainstalowane wszystkie wstępnie wymagane składniki na komputerze; należy ręcznie zainstalować wszystkie wymagania wstępne. Skrypty są przeznaczone głównie dla ustawienie serwery kompilacji lub gdy chcesz zainstalować narzędzia bez uprawnień administratora (Uwaga zastrzeżenie: wymagania wstępne powyżej). Więcej informacji można znaleźć na [zainstalować temat referencyjny skryptu](tools/dotnet-install-script.md). Jeśli interesuje Cię sposobu konfigurowania zestawu SDK na serwerze kompilacji elementu konfiguracji może potrwać przyjrzeć się [zestawu SDK z serwerami CI](tools/using-ci-with-cli.md) dokumentu. 

Domyślnie zestaw SDK zainstaluje w sposób "side-by-side" (SxS). Oznacza to, że wiele wersji narzędzi interfejsu wiersza polecenia mogą współistnieć na jednym komputerze w danym momencie. Pobiera używania poprawnej wersji to co omówiono bardziej szczegółowo w [sekcji sterowników](tools/index.md#driver) tematu narzędzi wiersza polecenia programu .NET Core.
