---
title: 'Błędy inicjowania programu .NET Framework: zarządzanie środowiskami użytkownika'
ms.date: 03/30/2017
helpviewer_keywords:
- no framework found experience
- initialization errors [.NET Framework]
- .NET Framework, initialization errors
ms.assetid: 680a7382-957f-4f6e-b178-4e866004a07e
ms.openlocfilehash: 73a0ffd4a39b144a61bf559ac424414728fb9a3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75716453"
---
# <a name="net-framework-initialization-errors-managing-the-user-experience"></a>Błędy inicjowania programu .NET Framework: zarządzanie środowiskami użytkownika

System aktywacji środowiska wykonawczego języka wspólnego (CLR) określa wersję środowiska CLR, która będzie używana do uruchamiania kodu aplikacji zarządzanej. W niektórych przypadkach system aktywacji może nie być w stanie znaleźć wersji programu CLR do załadowania. Taka sytuacja zazwyczaj występuje, gdy aplikacja wymaga wersji CLR, która jest nieprawidłowa lub nie zainstalowana na danym komputerze. Jeśli żądana wersja nie zostanie znaleziona, system aktywacji CLR zwraca kod błędu HRESULT z funkcji lub interfejsu, który został wywołany i może wyświetlić komunikat o błędzie do użytkownika, który uruchamia aplikację. Ten artykuł zawiera listę kodów HRESULT i wyjaśnia, jak można zapobiec wyświetlaniu komunikatu o błędzie.

ClR zapewnia infrastrukturę rejestrowania, aby pomóc w debugowaniu problemów z aktywacją CLR, zgodnie z opisem w [Jak: Debugowanie CLR problemy z aktywacją](how-to-debug-clr-activation-issues.md). Tej infrastruktury nie należy mylić z [dziennikami wiązania zestawu,](../tools/fuslogvw-exe-assembly-binding-log-viewer.md)które są zupełnie inne.

## <a name="clr-activation-hresult-codes"></a>Kody HRESULT aktywacji CLR

Interfejsy API aktywacji CLR zwracają kody HRESULT, aby zgłosić wynik operacji aktywacji do hosta. Hosty CLR powinny zawsze zapoznać się z tymi wartościami zwracania przed kontynuowaniem dodatkowych operacji.

- CLR_E_SHIM_RUNTIMELOAD

- CLR_E_SHIM_RUNTIMEEXPORT

- CLR_E_SHIM_INSTALLROOT

- CLR_E_SHIM_INSTALLCOMP

- CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND

- CLR_E_SHIM_SHUTDOWNINPROGRESS

## <a name="ui-for-initialization-errors"></a>Interfejs użytkownika dla błędów inicjowania

Jeśli system aktywacji CLR nie może załadować poprawnej wersji środowiska wykonawczego wymaganego przez aplikację, zostanie wyświetlony komunikat o błędzie dla użytkowników, aby poinformować ich, że ich komputer nie jest poprawnie skonfigurowany do uruchomienia aplikacji i zapewnia im komunikat o błędzie. możliwość naprawienia tej sytuacji. Następujący komunikat o błędzie jest zazwyczaj prezentowany w tej sytuacji. Użytkownik może wybrać **opcję Tak,** aby przejść do witryny firmy Microsoft w sieci Web, gdzie można pobrać poprawną wersję programu .NET Framework dla aplikacji.

![Okno dialogowe Błąd inicjowania programu .NET Framework](./media/initialization-errors-managing-the-user-experience/initialization-error-dialog.png "Typowy komunikat o błędzie dla błędów inicjowania")

## <a name="resolving-the-initialization-error"></a>Rozwiązywanie problemu inicjowania

Jako deweloper masz wiele opcji kontrolowania komunikatu o błędzie inicjowania programu .NET Framework. Na przykład można użyć flagi interfejsu API, aby zapobiec wyświetlaniu wiadomości, jak omówiono w następnej sekcji. Jednak nadal trzeba rozwiązać problem, który uniemożliwił aplikacji ładowanie żądanego środowiska uruchomieniowego. W przeciwnym razie aplikacja może nie działać w ogóle lub niektóre funkcje mogą być niedostępne.

Aby rozwiązać podstawowe problemy i zapewnić najlepsze środowisko użytkownika (mniej komunikatów o błędach), zalecamy następujące czynności:

- W przypadku aplikacji .NET Framework 3.5 (i wcześniejszych): skonfiguruj aplikację do obsługi wersji programu .NET Framework 4 lub nowszych (zobacz [instrukcje).](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)

- Dla aplikacji .NET Framework 4: Zainstaluj pakiet redystrybucyjny .NET Framework 4 jako część konfiguracji aplikacji. Zobacz [Przewodnik wdrażania dla deweloperów](deployment-guide-for-developers.md).

## <a name="controlling-the-error-message"></a>Kontrolowanie komunikatu o błędzie

Wyświetlanie komunikatu o błędzie informującego, że nie znaleziono żądanej wersji programu .NET Framework, można wyświetlić jako pomocną usługę lub niewielką irytację dla użytkowników. W obu przypadkach można kontrolować ten interfejs użytkownika, przekazując flagi do interfejsów API aktywacji.

[Metoda ICLRMetaHostPolicy::GetRequestedRuntime](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) akceptuje [element](../unmanaged-api/hosting/metahost-policy-flags-enumeration.md) członkowski METAHOST_POLICY_FLAGS wyliczenia jako dane wejściowe. Możesz dołączyć flagę METAHOST_POLICY_SHOW_ERROR_DIALOG, aby zażądać komunikatu o błędzie, jeśli żądana wersja programu CLR nie zostanie znaleziona. Domyślnie komunikat o błędzie nie jest wyświetlany. (Metoda [ICLRMetaHost::GetRuntime](../unmanaged-api/hosting/iclrmetahost-getruntime-method.md) nie akceptuje tej flagi i nie udostępnia innego sposobu wyświetlania komunikatu o błędzie).

System Windows udostępnia [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) funkcja, której można użyć do zadeklarowania, czy mają być wyświetlane komunikaty o błędach w wyniku kodu, który działa w ramach procesu. Można określić flagę SEM_FAILCRITICALERRORS, aby zapobiec wyświetlaniu komunikatu o błędzie.

Jednak w niektórych scenariuszach ważne jest, aby zastąpić ustawienie SEM_FAILCRITICALERRORS ustawione przez proces aplikacji. Na przykład jeśli masz natywnego składnika COM, który obsługuje środowisko CLR i który jest hostowany w procesie, w którym ustawiono SEM_FAILCRITICALERRORS, można zastąpić flagę, w zależności od wpływu wyświetlania komunikatów o błędach w ramach tego konkretnego procesu aplikacji. W takim przypadku można użyć jednej z następujących flag, aby zastąpić SEM_FAILCRITICALERRORS:

- Użyj METAHOST_POLICY_IGNORE_ERROR_MODE z [ICLRMetaHostPolicy::GetRequestedRuntime](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metody.

- Użyj RUNTIME_INFO_IGNORE_ERROR_MODE z funkcją [GetRequestedRuntimeInfo.](../unmanaged-api/hosting/getrequestedruntimeinfo-function.md)

## <a name="ui-policy-for-clr-provided-hosts"></a>Zasady interfejsu użytkownika dla hostów dostarczonych przez program CLR

Środowisko CLR zawiera zestaw hostów dla różnych scenariuszy, a wszystkie te hosty wyświetlają komunikat o błędzie, gdy napotkają problemy z ładowaniem wymaganej wersji środowiska wykonawczego. Poniższa tabela zawiera listę hostów i ich zasady komunikatów o błędach.

|Host CLR|Opis|Zasady komunikatów o błędach|Czy można wyłączyć komunikat o błędzie?|
|--------------|-----------------|--------------------------|------------------------------------|
|Zarządzany host EXE|Uruchamia zarządzane exes.|Jest wyświetlany w przypadku braku wersji programu .NET Framework|Nie|
|Zarządzany host COM|Ładuje zarządzane składniki COM do procesu.|Jest wyświetlany w przypadku braku wersji programu .NET Framework|Tak, ustawiając flagę SEM_FAILCRITICALERRORS|
|ClickOnce hosta|Uruchamia aplikacje ClickOnce.|Jest wyświetlany w przypadku braku wersji programu .NET Framework, począwszy od programu .NET Framework 4.5|Nie|
|Host XBAP|Uruchamia aplikacje WPF XBAP.|Jest wyświetlany w przypadku braku wersji programu .NET Framework, począwszy od programu .NET Framework 4.5|Nie|

## <a name="windows-8-behavior-and-ui"></a>Zachowanie i interfejs użytkownika systemu Windows 8

System aktywacji CLR zapewnia takie samo zachowanie i interfejs użytkownika w systemie Windows 8, jak w przypadku innych wersji systemu operacyjnego Windows, z wyjątkiem sytuacji, gdy napotka problemy z ładowaniem programu CLR 2.0. System Windows 8 zawiera program .NET Framework 4.5, który używa programu CLR 4.5. Jednak system Windows 8 nie zawiera programu .NET Framework 2.0, 3.0 lub 3.5, które używają programu CLR 2.0. W rezultacie aplikacje zależne od programu CLR 2.0 domyślnie nie są uruchamiane w systemie Windows 8. Zamiast tego wyświetlają następujące okno dialogowe, aby umożliwić użytkownikom zainstalowanie programu .NET Framework 3.5. Użytkownicy mogą również włączyć program .NET Framework 3.5 w Panelu sterowania. Obie opcje zostały omówione w artykule [Zainstaluj program .NET Framework 3.5 w systemach Windows 10, Windows 8.1 i Windows 8](../install/dotnet-35-windows-10.md).

![Okno dialogowe dla instalacji 3.5 w systemie Windows 8](./media/initialization-errors-managing-the-user-experience/install-framework-on-demand-dialog.png "Monitowanie o zainstalowanie programu .NET Framework 3.5 na żądanie")

> [!NOTE]
> .NET Framework 4.5 zastępuje .NET Framework 4 (CLR 4) na komputerze użytkownika. W związku z tym aplikacje .NET Framework 4 działają bezproblemowo, bez wyświetlania tego okna dialogowego w systemie Windows 8.

Po zainstalowaniu programu .NET Framework 3.5 użytkownicy mogą uruchamiać aplikacje zależne od programu .NET Framework 2.0, 3.0 lub 3.5 na swoich komputerach z systemem Windows 8. Można również uruchomić aplikacje .NET Framework 1.0 i 1.1, pod warunkiem, że te aplikacje nie są jawnie skonfigurowane do uruchamiania tylko w programie .NET Framework 1.0 lub 1.1. Zobacz [Migrowanie z programu .NET Framework 1.1](../migration-guide/migrating-from-the-net-framework-1-1.md).

Począwszy od programu .NET Framework 4.5, usprawniono rejestrowanie aktywacji CLR, aby uwzględnić wpisy dziennika, które rejestrują, kiedy i dlaczego wyświetlany jest komunikat o błędzie inicjowania. Aby uzyskać więcej informacji, zobacz [Jak: Problemy z aktywacją programu Debug clr](how-to-debug-clr-activation-issues.md).

## <a name="see-also"></a>Zobacz też

- [Przewodnik wdrażania dla deweloperów](deployment-guide-for-developers.md)
- [Jak: Konfigurowanie aplikacji do obsługi wersji programu .NET Framework 4 lub nowszych](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Instrukcje: Debugowanie problemów aktywacji środowiska CLR](how-to-debug-clr-activation-issues.md)
- [Instalowanie programu .NET Framework 3.5 w systemie Windows 10, Windows 8.1 lub Windows 8](../install/dotnet-35-windows-10.md)
