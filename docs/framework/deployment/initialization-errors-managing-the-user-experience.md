---
title: 'Błędy inicjowania programu .NET framework: Zarządzanie wrażeniami użytkownika'
ms.date: 03/30/2017
helpviewer_keywords:
- no framework found experience
- initialization errors [.NET Framework]
- .NET Framework, initialization errors
ms.assetid: 680a7382-957f-4f6e-b178-4e866004a07e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8e5a3cb79187d6434585560e9c128e03fe8003b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646127"
---
# <a name="net-framework-initialization-errors-managing-the-user-experience"></a>Błędy inicjowania programu .NET framework: Zarządzanie wrażeniami użytkownika

Wspólny system aktywacji języka wspólnego (CLR) określa wersję środowiska CLR, która będzie służyć do uruchamiania kodu aplikacji zarządzanej. W niektórych przypadkach system aktywacji nie można odnaleźć wersji środowiska CLR do załadowania. Ta sytuacja występuje zwykle w przypadku, gdy aplikacja wymaga wersji środowiska CLR, która jest nieprawidłowa lub nie została zainstalowana na danym komputerze. Jeśli żądana wersja nie zostanie znaleziony, system aktywacji środowiska CLR zwraca kod błędu HRESULT z funkcji lub interfejs, który został wywołany i może być wyświetlany komunikat o błędzie do użytkownika, który uruchomił aplikację. Ten artykuł zawiera listę kodów HRESULT i wyjaśniono, jak można zapobiec komunikat o błędzie są wyświetlane.

Środowisko CLR oferuje infrastrukturę rejestrowania, aby ułatwić debugowanie problemów aktywacji środowiska CLR, zgodnie z opisem w [jak: Debugowanie problemów aktywacji środowiska CLR](../../../docs/framework/deployment/how-to-debug-clr-activation-issues.md). Ta infrastruktura nie należy mylić z [dzienniki powiązań zestawów](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), które są zupełnie innego.

## <a name="clr-activation-hresult-codes"></a>Kody HRESULT aktywacji środowiska CLR

Aktywacja CLR interfejsów API zwraca wartość HRESULT kody do zgłaszania wynik operacji aktywacji do hosta. Hosty środowiska CLR zawsze powinni konsultować się te wartości zwracane, przed wykonaniem dodatkowych operacji.

- CLR_E_SHIM_RUNTIMELOAD

- CLR_E_SHIM_RUNTIMEEXPORT

- CLR_E_SHIM_INSTALLROOT

- CLR_E_SHIM_INSTALLCOMP

- CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND

- CLR_E_SHIM_SHUTDOWNINPROGRESS

## <a name="ui-for-initialization-errors"></a>Błędy inicjowania interfejsu użytkownika

Jeśli system aktywacji środowiska CLR nie można załadować poprawną wersję środowiska uruchomieniowego, które jest wymagane przez aplikację, wyświetla komunikat o błędzie do użytkowników i poinformuj ich o tym komputerze nie jest prawidłowo skonfigurowany do uruchamiania aplikacji i udostępnia je za pomocą możliwości, aby rozwiązać ten problem. Następujący komunikat o błędzie, zazwyczaj są przedstawione w tej sytuacji. Użytkownik może wybrać **tak** można przejść do witryny firmy Microsoft, w którym będą oni mogli pobrać poprawną wersję .NET Framework dla aplikacji.

![Okno dialogowe Błąd inicjalizacji programu .NET framework](./media/initialization-errors-managing-the-user-experience/initialization-error-dialog.png "komunikat o błędzie typowe błędy inicjowania")

## <a name="resolving-the-initialization-error"></a>Błąd podczas inicjowania rozpoznawania

Jako deweloper masz różne opcje do kontrolowania komunikat o błędzie inicjowania środowiska .NET Framework. Na przykład można użyć flagi interfejsu API aby zapobiec wiadomości są wyświetlane zgodnie z opisem w następnej sekcji. Jednak nadal trzeba rozwiązać ten problem uniemożliwiający ładowanie żądanego środowiska uruchomieniowego aplikacji. W przeciwnym razie aplikacja może nie działać w ogóle lub niektóre funkcje mogą nie być dostępne.

Aby rozwiązać podstawowe problemy i zapewniają najlepsze środowisko użytkownika (mniej komunikaty o błędach), zalecamy wykonanie poniższych czynności:

- W przypadku środowiska .NET Framework 3.5 (i starszych) aplikacji: Konfigurowanie aplikacji do obsługi programu .NET Framework 4 lub nowszej wersji (zobacz [instrukcje](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)).

- W przypadku aplikacji .NET Framework 4: Zainstaluj pakiet redystrybucyjny programu .NET Framework 4, jako część ustawień aplikacji. Zobacz [przewodnik wdrażania dla deweloperów](../../../docs/framework/deployment/deployment-guide-for-developers.md).

## <a name="controlling-the-error-message"></a>Kontrolowanie komunikat o błędzie

Wyświetlanie komunikatu o błędzie do komunikowania się nie znaleziono żądanej wersji .NET Framework mogą być wyświetlane jako pomocny usługi lub pomocniczych określenia dokuczliwości dla użytkowników. W obu przypadkach można kontrolować tego interfejsu użytkownika przez przekazanie flagi aktywacji interfejsów API.

[Iclrmetahostpolicy::getrequestedruntime —](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metoda przyjmuje [metahost_policy_flags —](../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) element członkowski wyliczenia jako dane wejściowe. Może zawierać flagi METAHOST_POLICY_SHOW_ERROR_DIALOG żądania komunikat o błędzie, jeśli nie można odnaleźć żądanej wersji środowiska CLR. Komunikat o błędzie nie jest wyświetlana domyślnie. ( [Iclrmetahost::getruntime —](../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) metody nie akceptuje tej flagi, a nie zapewnia inny sposób, aby wyświetlić komunikat o błędzie.)

Windows oferuje [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkID=255242) funkcja, która służy do deklarowania, czy chcesz, aby komunikaty o błędach do wyświetlenia wyniku kod, który jest uruchamiany w ramach procesu. Można określić flagę SEM_FAILCRITICALERRORS, aby uniemożliwić wyświetlenie komunikatu o błędzie.

Jednak w niektórych przypadkach warto zastąpić ustawienie SEM_FAILCRITICALERRORS ustawione przez proces aplikacji. Na przykład jeśli natywnych składnika modelu COM obsługujący środowiska CLR i który znajduje się w procesie, w którym SEM_FAILCRITICALERRORS je nastaven, możesz zastąpić flagi, w zależności od wpływu wyświetlanie komunikatów o błędach w ramach tego procesu określonej aplikacji. W takim przypadku służy jedną z następujących flag do zastąpienia SEM_FAILCRITICALERRORS:

- Użyj METAHOST_POLICY_IGNORE_ERROR_MODE z [iclrmetahostpolicy::getrequestedruntime —](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metody.

- Użyj RUNTIME_INFO_IGNORE_ERROR_MODE z [getrequestedruntimeinfo —](../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md) funkcji.

## <a name="ui-policy-for-clr-provided-hosts"></a>Zasady interfejsu użytkownika dla hostów, dostarczone przez CLR

Środowisko CLR obejmuje zestawu hostów dla różnych scenariuszy, a te wszystkie hosty wyświetlany komunikat o błędzie, gdy występują problemy podczas ładowania wymaganą wersję środowiska uruchomieniowego. Poniższa tabela zawiera listę hostów i ich zasadami komunikat o błędzie.

|Host aparatu CLR|Opis|Zasady wiadomości błędu|Można wyłączyć komunikat o błędzie?|
|--------------|-----------------|--------------------------|------------------------------------|
|Zarządzany host EXE|Uruchamia zarządzanych plików exe.|Jest wyświetlana w przypadku brakującą wersję .NET Framework|Nie|
|Zarządzany host COM|Ładunki zarządzane składniki COM do procesu.|Jest wyświetlana w przypadku brakującą wersję .NET Framework|Tak, ustawiając SEM_FAILCRITICALERRORS Flaga|
|ClickOnce host|Powoduje uruchomienie aplikacji ClickOnce.|Jest wyświetlana w przypadku brakujących wersji programu .NET Framework, począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]|Nie|
|XBAP host|Powoduje uruchomienie aplikacji WPF XBAP.|Jest wyświetlana w przypadku brakujących wersji programu .NET Framework, począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]|Nie|

## <a name="windows-8-behavior-and-ui"></a>Zachowanie systemu Windows 8 i interfejsu użytkownika

System aktywacji środowiska CLR zawiera te same zachowanie i interfejsu użytkownika po [!INCLUDE[win8](../../../includes/win8-md.md)] tak samo jak na inne wersje systemu operacyjnego Windows, z wyjątkiem po napotkaniu problemy z ładowaniem środowisko CLR 2.0. [!INCLUDE[win8](../../../includes/win8-md.md)] obejmuje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], który używa funkcji CLR 4.5. Jednak [!INCLUDE[win8](../../../includes/win8-md.md)] nie zawiera programu .NET Framework 2.0, 3.0 lub 3.5, która za pomocą wersji CLR 2.0. W rezultacie aplikacje, które są zależne od wersji CLR 2.0 nie należy uruchamiać na [!INCLUDE[win8](../../../includes/win8-md.md)] domyślnie. Zamiast tego są wyświetlane następujące okno dialogowe, aby umożliwić użytkownikom instalowanie programu .NET Framework 3.5. Użytkowników można również włączyć program .NET Framework 3.5 w Panelu sterowania. Obie opcje zostały omówione w artykule [Instalowanie programu .NET Framework 3.5 w systemie Windows 10, Windows 8.1 i Windows 8](../../../docs/framework/install/dotnet-35-windows-10.md).

![Okno dialogowe instalacji wersji 3.5 w systemie Windows 8](./media/initialization-errors-managing-the-user-experience/install-framework-on-demand-dialog.png "wybór opcji Monituj o zainstalowanie programu .NET Framework 3.5 na żądanie")

> [!NOTE]
> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Zastępuje programu .NET Framework 4 (Środowisko CLR 4) na komputerze użytkownika. W związku z tym, .NET Framework 4, aplikacje są uruchamiane bezproblemowo, bez wyświetlania tego okna dialogowego w [!INCLUDE[win8](../../../includes/win8-md.md)].

Po zainstalowaniu programu .NET Framework 3.5, użytkownicy mogą uruchamiać aplikacje zależne od programu .NET Framework 2.0, 3.0 lub 3.5 ich [!INCLUDE[win8](../../../includes/win8-md.md)] komputerów. Zadania mogą także uruchamiane .NET Framework 1.0 i 1.1 aplikacji, pod warunkiem, że te aplikacje nie są jawnie skonfigurowane do uruchamiania tylko na .NET Framework 1.0 i 1.1. Zobacz [migracji z programu .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).

Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], rejestrowanie aktywacji środowiska CLR został ulepszony, aby dołączyć wpisy dziennika, służące do rejestrowania, kiedy i dlaczego jest wyświetlany komunikat o błędzie inicjowania. Aby uzyskać więcej informacji, zobacz [jak: Debugowanie problemów aktywacji środowiska CLR](../../../docs/framework/deployment/how-to-debug-clr-activation-issues.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik wdrażania dla deweloperów](../../../docs/framework/deployment/deployment-guide-for-developers.md)
- [Instrukcje: Konfigurowanie aplikacji do obsługi w programie .NET Framework 4 lub nowszy](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Instrukcje: Debugowanie problemów aktywacji środowiska CLR](../../../docs/framework/deployment/how-to-debug-clr-activation-issues.md)
- [Instalowanie programu .NET Framework 3.5 w systemie Windows 10, Windows 8.1 lub Windows 8](../../../docs/framework/install/dotnet-35-windows-10.md)