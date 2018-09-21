---
title: Uruchamianie aplikacji konsoli na platformie Docker
description: Dowiedz się, jak wykonać istniejącą aplikację konsoli .NET Framework i uruchomienia jej w kontenerze platformy Docker Windows.
author: spboyer
ms.date: 09/28/2016
ms.assetid: 85cca1d5-c9a4-4eb2-93e6-4f878de07fd7
ms.openlocfilehash: f5a38ac63db969a58e920ea79bf4bf10bcfcf64f
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46485616"
---
# <a name="running-console-applications-in-windows-containers"></a>Uruchamianie aplikacji konsoli w kontenerach Windows

Aplikacje konsoli służą wielu celom; zadania przetwarzania prostego zapytania stanu długotrwałej obraz dokumentu. W każdym przypadku możliwość uruchamiania i skalować te aplikacje są spełnione, mają ograniczenia nabycia sprzętu, czasu uruchamiania lub uruchamianie wielu wystąpień.

Kontenery przenosicie aplikacje konsoli, aby używać platformy Docker i systemu Windows Server umożliwia uruchamianie tych aplikacji z stanu czystego, umożliwiając im wykonywanie operacji, a następnie zamknięcie nie pozostawia żadnych śladów. W tym temacie opisano kroki niezbędne do przenoszenia aplikacji konsoli aby Windows na podstawie kontenera i uruchomić go za pomocą skryptu programu PowerShell.

Przykładowa aplikacja konsolowa to prosty przykład, w tym przypadku przyjmuje argument, pytanie, która zwraca losowych odpowiedzi. Może to potrwać `customer_id` i przetwarzanie ich podatków, lub Utwórz Miniatura `image_url` argumentu.

Oprócz odpowiedzi `Environment.MachineName` została dodana do odpowiedzi do pokazania różnicy między uruchomieniem aplikacji lokalnie i w kontenerze Windows. Po uruchomieniu aplikacji lokalnie, ma zostać zwrócony Twojej nazwy komputera lokalnego i uruchamianego w kontenerze Windows; Identyfikator sesji kontenera jest zwracana.

[Kompletny przykład](https://github.com/dotnet/samples/tree/master/framework/docker/ConsoleRandomAnswerGenerator) jest dostępny w repozytorium dotnet/samples w witrynie GitHub. Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Musisz znać niektóre platformy Docker warunki przed rozpoczęciem pracy nad przeniesieniem aplikacji do kontenera.

> A *obrazu platformy Docker* jest tylko do odczytu szablonu, który definiuje środowisko działający kontener, w tym systemu operacyjnego (OS), składników systemu i aplikacji.

Jedną z ważnych funkcji obrazów platformy Docker jest, że obrazy składają się z obrazu podstawowego. Każdy nowy obraz dodaje niewielkim zestawie funkcji do istniejącego obrazu. 

> A *kontener platformy Docker* jest uruchomione wystąpienie obrazu. 

Skalowanie aplikacji przez uruchomienie tego samego obrazu w wielu kontenerach.
Model jest podobny do uruchamiania tej samej aplikacji na wielu hostach.

Znajdziesz się więcej o architekturze platformy Docker, zapoznając się [Docker — omówienie](https://docs.docker.com/engine/understanding-docker/) w witrynie platformy Docker. 

Przenoszenie aplikacji konsoli polega na kilka kroków.

1. [Kompiluj aplikację](#building-the-application)
1. [Tworzenie pliku Dockerfile obrazu](#creating-the-dockerfile)
1. [Proces, aby skompilować i uruchomić kontener platformy Docker](#creating-the-image)

## <a name="prerequisites"></a>Wymagania wstępne
Kontenery Windows są obsługiwane na [Rocznicowej aktualizacji systemu Windows 10](https://www.microsoft.com/en-us/software-download/windows10/) lub [systemu Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server).

> [!NOTE]
>Jeśli używasz systemu Windows Server 2016, należy włączyć kontenerów ręcznie, ponieważ Instalator Windows dla Docker nie włączy tę funkcję. Upewnij się, że wszystkie aktualizacje zostały uruchomione dla systemu operacyjnego, a następnie postępuj zgodnie z instrukcjami [wdrażania hosta kontenera](https://msdn.microsoft.com/virtualization/windowscontainers/deployment/deployment) artykuł, aby zainstalować kontenerów i funkcje platformy Docker.

Musisz mieć Docker for Windows, wersja 1.12 26 lub nowszej wersji Beta do obsługi Windows kontenery. Domyślnie program Docker umożliwia kontenerów opartych na systemie Linux; Przełącz się do kontenerów Windows, klikając prawym przyciskiem myszy ikonę platformy Docker, na pasku zadań, a następnie wybierz pozycję **przełączyć się do kontenerów Windows**. Docker uruchomi proces zmiany i może być wymagane ponowne uruchomienie.

![Windows-Containers](./media/console/SwitchContainer.png)

## <a name="building-the-application"></a>Tworzenie aplikacji
Zazwyczaj aplikacje konsoli są dystrybuowane za pośrednictwem Instalatora, FTP lub udziału plików wdrożenia. Podczas wdrażania do kontenera, zasoby muszą być kompilowane i umieszczane w lokalizacji, która może być używany podczas tworzenia obrazu platformy Docker.

W *build.ps1*, skrypt używa [MSBuild](/visualstudio/msbuild/msbuild) skompilować aplikację, aby ukończyć zadanie tworzenia zasobów. Istnieje kilka parametrów przekazywanych do programu MSBuild, aby zakończyć potrzebne zasoby. Nazwa pliku projektu lub rozwiązania jest kompilowana, lokalizację dla danych wyjściowych, a na koniec konfiguracji (wydania lub debugowania).

W wywołaniu `Invoke-MSBuild` `OutputPath` ustawiono **publikowania** i `Configuration` równa **wersji**. 

```
function Invoke-MSBuild ([string]$MSBuildPath, [string]$MSBuildParameters) {
    Invoke-Expression "$MSBuildPath $MSBuildParameters"
}

Invoke-MSBuild -MSBuildPath "MSBuild.exe" -MSBuildParameters ".\ConsoleRandomAnswerGenerator.csproj -p:OutputPath=.\publish -p:Configuration=Release"
```

## <a name="creating-the-dockerfile"></a>Tworzenie pliku Dockerfile
Obraz podstawowy, używany do konsoli aplikacji .NET Framework jest `microsoft/windowsservercore`, publicznie dostępny w [usługi Docker Hub](https://hub.docker.com/r/microsoft/windowsservercore/). Obraz podstawowy zawiera minimalnej instalacji systemu Windows Server 2016, .NET Framework 4.6.2 i służy jako podstawowy obraz systemu operacyjnego dla kontenerów Windows.

```
FROM microsoft/windowsservercore
ADD publish/ /
ENTRYPOINT ConsoleRandomAnswerGenerator.exe
```
Pierwszy wiersz w pliku Dockerfile wyznacza przy użyciu obrazu podstawowego [ `FROM` ](https://docs.docker.com/engine/reference/builder/#/from) instrukcji. Następnie [ `ADD` ](https://docs.docker.com/engine/reference/builder/#/add) w pliku kopiuje zasoby aplikacji z **publikowania** folderu do folderu głównego kontenera i ostatnie; ustawienie [ `ENTRYPOINT` ](https://docs.docker.com/engine/reference/builder/#/entrypoint) stanów obrazu tego to polecenie lub aplikacji, która będzie uruchamiana po uruchomieniu kontenera. 

## <a name="creating-the-image"></a>Tworzenie obrazu
Aby utworzyć obraz platformy Docker, poniższy kod jest dodawany do *build.ps1* skryptu. Po uruchomieniu skryptu `console-random-answer-generator` obrazu jest tworzony przy użyciu zasobów skompilowane z programu MSBuild zdefiniowane w [Kompilowanie aplikacji](#building-the-application) sekcji.

```powershell
$ImageName="console-random-answer-generator"

function Invoke-Docker-Build ([string]$ImageName, [string]$ImagePath, [string]$DockerBuildArgs = "") {
    echo "docker build -t $ImageName $ImagePath $DockerBuildArgs"
    Invoke-Expression "docker build -t $ImageName $ImagePath $DockerBuildArgs"
}

Invoke-Docker-Build -ImageName $ImageName -ImagePath "."
```

Uruchom skrypt, używając `.\build.ps1` w wierszu polecenia programu PowerShell.

Po zakończeniu kompilacji przy użyciu `docker images` polecenie z wiersza polecenia lub w wierszu polecenia programu PowerShell; zobaczysz, że obraz jest utworzona i gotowa do uruchomienia.

```
REPOSITORY                        TAG                 IMAGE ID            CREATED             SIZE
console-random-answer-generator   latest              8f7c807db1b5        8 seconds ago       7.33 GB
```

## <a name="running-the-container"></a>Uruchamianie kontenera
Kontener można uruchomić z wiersza polecenia, używając poleceń Docker.

```
docker run console-random-answer-generator "Are you a square container?"
```

Dane wyjściowe są

```
The answer to your question: 'Are you a square container?' is Concentrate and ask again on (70C3D48F4343)
```

Jeśli uruchamiasz `docker ps -a` polecenia za pomocą programu PowerShell, możesz zobaczyć, czy kontener nadal istnieje.

```
CONTAINER ID        IMAGE                             COMMAND                  CREATED             STATUS                          
70c3d48f4343        console-random-answer-generator   "cmd /S /C ConsoleRan"   2 minutes ago       Exited (0) About a minute ago      
```

Kolumna stanu jest wyświetlany "około minutę temu", aplikacja jest kompletna i może zostać zamknięty. Tego polecenia kilkaset razy, będzie mieć sto statycznej po lewej stronie kontenerów za pomocą nie zadania do wykonania. W tym scenariuszu początku idealne operacja zakończyła się do pracy i zamknięcie lub czyszczenia. Aby osiągnąć ten przepływ pracy dodawania `--rm` opcję `docker run` polecenie spowoduje usunięcie kontenera zaraz `Exited` sygnału.

```
docker run --rm console-random-answer-generator "Are you a square container?"
```

Uruchomienie polecenia przy użyciu tej opcji, a następnie sprawdzając w danych wyjściowych `docker ps -a` polecenie; Zwróć uwagę, że identyfikator kontenera ( `Environment.MachineName`) nie jest na liście.

### <a name="running-the-container-using-powershell"></a>Uruchamianie kontenera przy użyciu programu PowerShell
W przykładowych plików projektu jest również *run.ps1* który znajduje się przykład jak używać programu PowerShell do uruchamiania aplikacji akceptuje argumenty.

Aby uruchomić, Otwórz program PowerShell i użyj następującego polecenia:

```
.\run.ps1 "Is this easy or what?"
```

## <a name="summary"></a>Podsumowanie
Po prostu przez dodanie pliku Dockerfile i publikowanie aplikacji, konteneryzuj swoje aplikacje konsoli .NET Framework i teraz uruchamiania wielu wystąpień, czystego uruchomienia i zatrzymania i więcej możliwości systemu Windows Server 2016 bez konieczności szukania dowolny skorzystać na wszystkich zmian w kodzie aplikacji.
