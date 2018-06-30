---
title: Migrowanie aplikacji starszych wbudowanymi .NET Framework do kontenerów systemu Windows
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Migrowanie aplikacji starszych wbudowanymi .NET Framework do kontenerów systemu Windows
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 01b84d29a559bde02ebd30535488c272d5208167
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106518"
---
# <a name="migrating-legacy-monolithic-net-framework-applications-to-windows-containers"></a>Migrowanie aplikacji starszych wbudowanymi .NET Framework do kontenerów systemu Windows

*Kontenery systemu Windows mogą być używane jako sposób do poprawy programowanie i testowanie środowiska i wdrażania aplikacji, które są oparte na starszych technologii .NET Framework, takich jak Web* *formularzy. Używanie kontenerów dla starszych aplikacji w ten sposób jest określana jako scenariusza "przyrostu i shift".*

Wcześniejszych sekcjach tego przewodnika ma branżowa architektura mikrousług, gdzie aplikacje biznesowe są rozmieszczone w różnych kontenerów. każdy z usługą małe, ukierunkowanych. Ten cel ma wiele korzyści. W nowo tworzonym tego podejścia jest zdecydowanie zalecane. Aplikacje krytyczne dla przedsiębiorstwa również korzystać do ponoszenie kosztów rearchitecture i ponowna implementacja.

Jednak nie wszystkie aplikacje będą korzystać do ponoszenie kosztów. Nie oznacza że nie można użyć tych aplikacji w scenariuszach kontenera.

W tej sekcji przeanalizujemy aplikacji dla eShopOnContainers wyświetlany w rysunek 7-1. Ta aplikacja będzie służyć przez członków zespołu enterprise eShopOnContainers do wyświetlania i edytowania katalogu produktów.

![](./media/image1.png)

**Rysunek 7-1**. Aplikacja formularzy sieci Web ASP.NET (technologia starsze) do kontenera systemu Windows

To jest aplikacja formularzy sieci Web, służący do przeglądania i modyfikowania wpisy w katalogu. Zależności formularzy sieci Web oznacza, że ta aplikacja nie będzie działać na .NET Core, chyba że jest napisany od nowa bez formularzy sieci Web i zamiast tego używa platformy ASP.NET Core MVC. Zobaczysz, jak można uruchomić aplikacji, takich jak te w kontenerach bez zmian. Widoczne będzie także, jak można zmienić minimalnego do pracy w trybie hybrydowego, w której niektóre funkcje został przeniesiony do oddzielnych mikrousługi, ale większość funkcji są wbudowanymi aplikacji.

## <a name="benefits-of-containerizing-a-monolithic-application"></a>Zalety containerizing wbudowanymi aplikacji

Aplikacja Catalog.WebForms jest dostępna w repozytorium GitHub eShopOnContainers (<https://github.com/dotnet/eShopOnContainers>). Ta aplikacja to aplikacja sieci web autonomiczny uzyskiwania dostępu do magazynu danych wysokiej dostępności. Mimo tego są zalety uruchamiania aplikacji w kontenerze. Możesz utworzyć obraz dla aplikacji. Od tego momentu każde wdrożenie jest uruchamiany w tym samym środowisku. Każdy kontener korzysta z tej samej wersji systemu operacyjnego, ma tę samą wersję zainstalowane zależności używa tej samej struktury i jest utworzony przy użyciu tego samego procesu. Widać aplikacji załadowany w Visual Studio 2017 na rysunku 7-2.

![](./media/image2.png)

**Rysunek 7-2**. Zarządzanie aplikacji formularzy sieci Web w programie Visual Studio 2017 katalogami

Ponadto deweloperzy wszystkie uruchomić aplikację w tym środowisku spójne. Problemy, które są wyświetlane tylko w niektórych wersjach pojawi się natychmiast dla deweloperów, a nie udostępniając w środowisku tymczasowym czy produkcyjnym. Różnice między środowisk deweloperskich między zespół deweloperów znaczenia mniej po aplikacje uruchamiane w kontenerach.

Na koniec konteneryzowanych aplikacje mają płaska krzywej skalowalnego w poziomie. Masz aplikacje jak konteneryzowanych zapamiętanych włączyć więcej kontenerów na maszynie wirtualnej lub więcej kontenerów na maszynie fizycznej. Przekłada się wyżej gęstości i mniej wymagane zasoby.

Z tego względu należy wziąć pod uwagę uruchamianie starszych aplikacji wbudowanymi w kontenerze Docker przy użyciu operacji "przyrostu i shift". Frazy "przyrostu i przesunięcia" opisuje zakres zadania: możesz *Podnieś* całej aplikacji z maszyny fizycznej lub wirtualnej, i *shift* go do kontenera. W sytuacjach idealne nie trzeba wprowadzać żadnych zmian do kodu aplikacji, aby uruchomić go w kontenerze.

## <a name="possible-migration-paths"></a>Ścieżki migracji możliwe

Jako aplikację wbudowanymi aplikacji Catalog.Webforms jest jednej aplikacji sieci web zawierający wszystkie kodu, w tym biblioteki dostępu do danych. Bazy danych są uruchamiane na osobnym komputerze wysokiej dostępności. Tej konfiguracji jest symulowane w przykładowym kodzie za pomocą usługi wykazu zasymulować: można uruchomić aplikacji Catalog.WebForms dla fałszywych danych do symulowania czysty scenariusz przyrostu shift. Oznacza to najprostsza ścieżka migracji, w której przenieść istniejące zasoby do uruchamiania w kontenerze bez wprowadzania żadnych zmian kodu w ogóle. Ta ścieżka jest odpowiedni dla aplikacji, które są kompletne i, która ma minimalne interakcje z funkcjami, który przenosisz mikrousług.

Jednak eShopOnContainers witryny sieci Web jest już dostęp do magazynu danych przy użyciu mikrousług dla różnych scenariuszy. Niektóre dodatkowe zmiany, małe możliwe do edytora katalogu wykorzystać mikrousługi katalogu zamiast bezpośrednie uzyskiwanie dostępu do magazynu danych katalogu.

Te zmiany pokazują kontynuacja do własnych aplikacji. Można wykonywać wszystkie przenoszenia istniejących aplikacji bez zmian do kontenerów do wprowadzania zmian w małych, umożliwiających istniejących aplikacji uzyskać dostęp do pewnych nowych mikrousług, aby całkowicie ponowne zapisywanie w pełni korzystać z nowej aplikacji Architektura mikrousługi. Prawidłowe ścieżki zależy od koszt migracji i korzysta z żadnych migracji.

## <a name="application-tour"></a>Samouczek aplikacji

Można załadować rozwiązania Catalog.WebForms i uruchomić aplikację jako aplikacja autonomiczna. W tej konfiguracji zamiast bazę danych magazynu trwałego aplikacji przy użyciu fałszywych usługi zwracanych danych. Aplikacja używa Autofac (<https://autofac.org/>) jako Inwersja kontroli (IOC) kontenera. Zależności Iniekcja można skonfigurować aplikacji na używanie fałszywych danych lub usługi data catalog na żywo. (Wyjaśnijmy więcej o Podpisane wkrótce.) Kod uruchomienia odczytuje ustawienie useFake z plików web.config i konfiguruje kontenera Autofac iniekcję usługę fałszywych danych lub usługa katalogowa na żywo. Po uruchomieniu aplikacji z useFake ustawiona na wartość false w pliku web.config, zobaczysz wyświetlanie danych wykazu aplikacji formularzy sieci Web.

Większość technik w tej aplikacji należy znać bardzo dla każdego, kto został użyty formularzy sieci Web. Jednak mikrousługi katalogu wprowadzono dwie metody, które mogą być nieznane: zależność Iniekcja, który został wcześniej wspomniano, i pracy z magazynami danych asynchronicznych w formularzach sieci Web.

Podpisane odwraca typowe strategii zorientowane obiektowo zapisywania klasy, które przydzielić wszystkich niezbędnych zasobów. Zamiast tego klasy żądania ich zależności z kontenera usług. Zaletą Podpisane jest, że można zastąpić usług zewnętrznych elementów sztucznych (mocks) do obsługi środowisk testowych lub innych.

Kontener Podpisane korzysta z konfiguracji appSettings pliku web.config do kontrolowania, czy używać katalogu fałszywych danych lub dane na żywo z uruchomionej usługi. Aplikacja rejestruje HttpModule obiektu, który tworzy kontener i rejestruje program obsługi żądania wstępnego wstrzyknięcia zależności. Można wyświetlić kod w pliku Modules/AutoFacHttpModule.cs, który wygląda jak w następującym przykładzie:

```cs
private static IContainer CreateContainer()
{
  // Configure AutoFac:
  // Register Containers:

  var settings = WebConfigurationManager.AppSettings;
  var useFake = settings["usefake"];
  bool fake = useFake == "true";
  var builder = new ContainerBuilder();

  if (fake)
  {
    builder.RegisterType<CatalogMockService>()
    .As<ICatalogService>();
  }
  else
  {
    builder.RegisterType<CatalogService>()
    .As<ICatalogService>();
    builder.RegisterType<RequestProvider>()
    .As<IRequestProvider>();
  }

  var container = builder.Build();
  return container;
}

private void InjectDependencies()
{
  if (HttpContext.Current.CurrentHandler is Page page)
  {
    // Get the code-behind class that we may have written
    var pageType = page.GetType().BaseType;

    // Determine if there is a constructor to inject, and grab it
    var ctor = (from c in pageType.GetConstructors()
                where c.GetParameters().Length > 0
                select c).FirstOrDefault();

    if (ctor != null)
    {
      // Resolve the parameters for the constructor
      var args = (from parm in ctor.GetParameters()
                  select Container.Resolve(parm.ParameterType))
                  .ToArray();

      // Execute the constructor method with the arguments resolved
      ctor.Invoke(page, args);
    }

    // Use the Autofac method to inject any
    // properties that can be filled by Autofac
    Container.InjectProperties(page);
  }
}
```

Strony aplikacji (Default.aspx.cs i EditPage.aspx.cs) definiować konstruktorów przyjmujących te zależności. Należy pamiętać, że domyślny konstruktor jest nadal istnieje i jest dostępny. Infrastruktura musi mieć następujący kod.

```cs
protected _Default() { }

public _Default(ICatalogService catalog) => this.catalog = catalog;
```

Wykaz interfejsów API są wszystkie asynchronicznej metody. Formularze sieci Web obsługuje teraz tych opcji dla wszystkich kontrolek danych. Aplikacja Catalog.WebForms listy używane powiązanie modelu i Edycja stron; formanty na stronach zdefiniuj SelectMethod, metody UpdateMethod InsertMethod i DeleteMethod właściwości, które określają umożliwiające zwracanie zadań operacji asynchronicznych. Formanty formularzy sieci Web zrozumieć, kiedy są asynchroniczne metody związany z formantem. Tylko ograniczenie wystąpią podczas używanie metod asynchronicznych select jest, że nie obsługuje stronicowania. Podpis stronicowania wymaga parametru wyjściowego i metody asynchroniczne nie mogą mieć parametrów out. Ta sama metoda jest używana w innych stron, które wymagają danych z usługi wykaz.

Konfigurację domyślną dla wykazu aplikacji formularzy sieci Web używa usługi catalog.api implementację testową. Ta makiety używa obiektu dataset ustalony danych, co upraszcza niektórych zadań przez usunięcie zależności od usługi catalog.api w środowiskach programistycznych.

## <a name="lifting-and-shifting"></a>Podnoszenia i przesuwanie

Visual Studio zapewnia obsługę dużą containerizing aplikacji. Kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz **Dodaj** i **Obsługa Docker**. Szablon projektu Docker dodaje nowy projekt w rozwiązaniu o nazwie **docker-tworzą**. Projekt zawiera zasoby Docker compose (lub kompilacji) obrazów należy i uruchamiania niezbędne kontenerów, jak pokazano na rysunku 7-3.

W najprostszej scenariuszach przyrostu i shift aplikacja będzie jednej usługi używanego dla aplikacji formularzy sieci Web. Szablon również zmieni Twój projekt startowy, aby wskazywał **rozwiązania docker compose** projektu. Teraz naciśnięcie klawisza Ctrl + F5 lub F5 tworzy obraz Docker i uruchamia kontenera Docker.

![](./media/image3.png)

**Rysunek 7-3**. **Rozwiązania docker compose** projektu w rozwiązaniu formularzy sieci Web

Przed uruchomieniem rozwiązania, należy się upewnić skonfigurowanie Docker do użycia kontenery systemu Windows. W tym celu należy kliknij prawym przyciskiem myszy ikonę na pasku zadań Docker w systemach Windows i wybierz **przełączyć się do systemu Windows kontenery**, jak pokazano na rysunku 7-4.

![](./media/image4.png)

**Rysunek 7-4**. Przełączanie do kontenerów systemu Windows z Docker ikona na pasku zadań systemu Windows

Jeśli element menu **przełączyć się do kontenerów Linux**, korzystasz już z Docker z kontenery systemu Windows.

Uruchamianie rozwiązania ponownym uruchomieniu hostów Docker. Podczas tworzenia, kompilowania aplikacji i Docker obrazu dla projektu formularzy sieci Web. Można to zrobić, po raz pierwszy zajmuje wiele czasu. Jest to spowodowane proces kompilacji pobiera podstawowy obraz systemu Windows Server i dodatkowe obrazu dla platformy ASP.NET. Kolejne kompilacji i cykli uruchamiania będzie znacznie szybsze.

Spójrzmy bardziej pliki dodane przez szablon projektu Docker. Kilka plików ono utworzone automatycznie. Visual Studio będzie korzystać do tworzenia obrazu Docker i kontener uruchamianie tych plików. Aby ręcznie uruchomić polecenia Docker, można użyć tych samych plików z poziomu interfejsu wiersza polecenia.

W poniższym przykładzie plik Dockerfile przedstawiono podstawowe ustawienia tworzenia obrazu Docker, na podstawie obrazu platformy ASP.NET w systemie Windows, uruchomioną witryny ASP.NET.

```
FROM microsoft/aspnet

ARG source

WORKDIR /inetpub/wwwroot

COPY ${source:-obj/Docker/publish} .
```

Ten plik Dockerfile będzie wyglądają bardzo podobnie do utworzonych na uruchamianie aplikacji platformy ASP.NET Core w kontenerach systemu Linux. Istnieje jednak kilka istotnych różnic. Najbardziej istotną różnicą jest to podstawowy obraz microsoft/aspnet, czyli bieżącego obrazu systemu Windows Server, który zawiera programu .NET Framework. Inne różnice są różne katalogi, skopiować z katalogu źródłowego.

Pliki w **docker-tworzą** projektu są potrzebne do tworzenia i konfigurowania kontenery zasoby Docker. Visual Studio umieszcza różne pliki docker-compose.yml w jeden węzeł, aby wyróżnić korzystania z nich. Plik podstawowy docker-compose zawiera dyrektywy, które są wspólne dla wszystkich konfiguracji. Plik docker-compose.override.yml zawiera zmienne środowiskowe i powiązane zastąpienia dewelopera konfiguracja. Wariantów o. vs.debug i. vs.release Podaj ustawienia środowiska, które umożliwiają Visual Studio, aby dołączyć do i zarządzanie nimi uruchomionych kontenera.

Podczas integracji z programem Visual Studio jest dodanie obsługi Docker do rozwiązania, możesz również skompilować i uruchomić z wiersza polecenia przy użyciu rozwiązania docker-tworzą zapasowej polecenia, jak przedstawiono w poprzednich sekcjach.

## <a name="getting-data-from-the-existing-catalog-net-core-microservice"></a>Pobieranie danych z istniejącego mikrousługi .NET Core katalogu

Można skonfigurować aplikacji formularzy sieci Web do używania mikrousługi katalogu eShopOnContainers można pobrać danych zamiast fałszywych danych. W tym celu należy zmodyfikować plik web.config i ustaw wartość klucza useFake na wartość false. Kontener Podpisane użyje klasy, która uzyskuje dostęp do mikrousługi katalogu na żywo, zamiast klasy, która zwraca dane ustalony. Niezbędne są inne zmiany kodu.

Uzyskiwanie dostępu do usługi katalogu na żywo oznacza należy zaktualizować **rozwiązania docker compose** projektu do tworzenia obrazu usługi katalogu i uruchom katalogu kontenera usług. CE docker dla systemu Windows obsługuje kontenery systemu Linux i kontenery systemu Windows, ale nie w tym samym czasie. Aby uruchomić mikrousługi katalogu, jest potrzebne do tworzenia obrazu, który uruchamia mikrousługi katalogu na górze kontenera usługi systemu Windows. Takie podejście wymaga inny plik Dockerfile dla projektu mikrousług niż przejrzane we wcześniejszych sekcjach. Plik Dockerfile.windows zawiera ustawienia konfiguracji, aby utworzyć obraz kontenera katalogu interfejsu API, dzięki czemu uruchamia się w kontenerze systemu Windows — na przykład, aby użyć obrazu systemu Windows Nano Docker.

Mikrousługi katalogu korzysta z bazy danych programu SQL Server. W związku z tym należy użyć do obrazu systemu Windows Docker serwera SQL.

Po wprowadzeniu tych zmian projektu docker-compose jest więcej, aby uruchomić aplikację. Projekt rozpocznie się teraz na serwerze SQL przy użyciu obrazu serwera SQL na podstawie systemu Windows. Mikrousługi katalogu rozpoczyna się w kontenerze systemu Windows. I również rozpoczyna kontenerze Edytor formularzy sieci Web wykazu w kontenerze systemu Windows. Jeśli obrazy potrzeby budynku, najpierw tworzone są obrazy.

## <a name="development-and-production-environments"></a>Środowiska deweloperskie i produkcji

Istnieje kilka różnic między konfiguracji Programowanie i produkcji. W środowisku programistycznym możesz uruchomić aplikacji formularzy sieci Web, katalogu mikrousługi i SQL Server w kontenerach systemu Windows w ramach tego samego hosta Docker. We wcześniejszych sekcjach wspomniano obrazów programu SQL Server wdrożony w tym samym hoście Docker jako inne na podstawie .NET Core usługi na hoście Docker opartych na systemie Linux. Zaletą uruchamiania wielu mikrousług w tym samym hoście Docker (lub klastra) jest o mniej komunikacji sieciowej i komunikacji między kontenery ma mniejsze opóźnienia.

W środowisku programistycznym możesz uruchomić wszystkie kontenery w tej samej wersji systemu operacyjnego. CE docker dla systemu Windows nie obsługuje uruchamiania kontenery z systemem Windows i Linux w tym samym czasie. W środowisku produkcyjnym można zdecydować, czy chcesz uruchomić mikrousługi katalogu w kontenerze systemu Windows w jednym Docker hosta (lub klastra) lub formularzy sieci Web aplikacji komunikują się z wystąpieniem mikrousługi katalogu uruchomione w kontenerze systemu Linux na inną Docker host. To zależy od sposobu Optymalizuj dla opóźnienia sieci. W większości przypadków ma mikrousług, które aplikacje są zależne od uruchomione w tym samym hoście Docker (lub swarm) w celu ułatwienia wdrażania oraz mniejsze opóźnienia komunikacji. W tych konfiguracjach tylko kosztowne komunikacji jest między wystąpieniami mikrousługi i serwery wysokiej dostępności dla magazynu danych.

>[!div class="step-by-step"]
[Poprzednie](../net-core-single-containers-linux-windows-server-hosts/index.md)
[dalej](../multi-container-microservice-net-applications/index.md)
