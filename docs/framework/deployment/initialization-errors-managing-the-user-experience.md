---
title: "Błędy inicjowania programu .NET Framework: zarządzanie wrażeniami użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- no framework found experience
- initialization errors [.NET Framework]
- .NET Framework, initialization errors
ms.assetid: 680a7382-957f-4f6e-b178-4e866004a07e
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d8679e930b1f12119211a6463289fb37a18692d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="net-framework-initialization-errors-managing-the-user-experience"></a>Błędy inicjowania programu .NET Framework: zarządzanie wrażeniami użytkownika
Wspólny system aktywacji języka wspólnego (CLR) określa wersję środowiska CLR, która będzie służyć do uruchamiania kodu aplikacji zarządzanych. W niektórych przypadkach system aktywacji nie można znaleźć wersji środowiska CLR do załadowania. Ta sytuacja zwykle występuje, gdy aplikacja wymaga wersji środowiska CLR, która jest nieprawidłowa lub nie została zainstalowana na danym komputerze. Jeśli nie odnaleziono żądanej wersji, system aktywacji CLR zwraca kod błędu HRESULT z funkcji lub interfejs, który został wywołany i może być wyświetlany komunikat o błędzie do użytkownika, który jest uruchomiona aplikacja. Ten artykuł zawiera listę kodów HRESULT i objaśniono, w jaki sposób można zapobiec komunikat o błędzie wyświetlany.  
  
 Środowisko CLR rejestrowania oferuje infrastrukturę służącą do pomóc w debugowaniu problemów aktywacji środowiska CLR, zgodnie z opisem w [porady: debugowanie problemów aktywacji środowiska CLR](../../../docs/framework/deployment/how-to-debug-clr-activation-issues.md). Ta infrastruktura nie należy mylić z [dzienniki powiązań zestawów](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), które są całkowicie innej.  
  
## <a name="clr-activation-hresult-codes"></a>Kody HRESULT aktywacji środowiska CLR  
 Aktywacja CLR interfejsów API zwraca kody HRESULT do zgłaszania wynik operacji aktywacji do hosta. Hosty CLR zawsze powinni skontaktować te wartości zwracanych przed wykonaniem dodatkowych operacji.  
  
-   CLR_E_SHIM_RUNTIMELOAD  
  
-   CLR_E_SHIM_RUNTIMEEXPORT  
  
-   CLR_E_SHIM_INSTALLROOT  
  
-   CLR_E_SHIM_INSTALLCOMP  
  
-   CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND  
  
-   CLR_E_SHIM_SHUTDOWNINPROGRESS  
  
## <a name="ui-for-initialization-errors"></a>Interfejs użytkownika dla błędy inicjowania  
 Jeśli system aktywacji środowiska CLR nie może załadować poprawną wersję środowiska uruchomieniowego, które jest wymagane przez aplikację, wyświetla komunikat o błędzie do użytkowników w celu poinformowania ich, że komputera nie jest prawidłowo skonfigurowana do uruchamiania aplikacji oraz udostępnia je za pomocą możliwość rozwiązać tę sytuację. W takiej sytuacji zwykle zobaczy następujący komunikat o błędzie. Użytkownik może wybrać **tak** można przejść do witryny firmy Microsoft, w którym mogą pobrać poprawną wersję .NET Framework dla aplikacji.  
  
 ![Okno dialogowe Błąd inicjowania programu .NET framework](../../../docs/framework/deployment/media/initerrordialog.png "InitErrorDialog")  
Typowym komunikatem o błędzie dla błędów inicjowania  
  
## <a name="resolving-the-initialization-error"></a>Błąd podczas inicjowania rozpoznawania  
 Deweloperzy masz różne opcje umożliwiające sterowanie komunikat o błędzie inicjowania .NET Framework. Na przykład umożliwia flagi interfejsu API uniemożliwić komunikat wyświetlany, zgodnie z opisem w następnej sekcji. Jednak nadal należy rozwiązać problem, który uniemożliwia załadowanie wymagane środowisko uruchomieniowe aplikacji. W przeciwnym razie aplikacja nie może działać w ogóle lub niektóre funkcje mogą nie być dostępne.  
  
 Aby rozwiązać problemy podstawowej i zapewnić najlepsze środowisko użytkownika (mniej komunikaty o błędach), zaleca się następujące czynności:  
  
-   W przypadku aplikacji .NET Framework 3.5 (i starszych): Konfigurowanie aplikacji do obsługi programu .NET Framework 4 lub 4.5 (zobacz [instrukcje](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)).  
  
-   W przypadku aplikacji .NET Framework 4: Zainstaluj pakiet redystrybucyjny programu .NET Framework 4 jako część konfiguracji aplikacji. Zobacz [przewodnik wdrażania dla deweloperów](../../../docs/framework/deployment/deployment-guide-for-developers.md).  
  
## <a name="controlling-the-error-message"></a>Kontrolowanie komunikat o błędzie  
 Wyświetlanie komunikat o błędzie do komunikacji nie znaleziono żądanej wersji .NET Framework można wyświetlić jako przydatne usługi lub drobne określenia dokuczliwości dla użytkowników. W obu przypadkach interfejs ten można kontrolować przez przekazanie flagi aktywacji interfejsów API.  
  
 [ICLRMetaHostPolicy::GetRequestedRuntime](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metoda przyjmuje [metahost_policy_flags —](../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) wyliczeniowego jako dane wejściowe. Może zawierać flagi METAHOST_POLICY_SHOW_ERROR_DIALOG poprosić komunikat o błędzie, jeśli nie odnaleziono żądanej wersji środowiska CLR. Domyślnie nie jest wyświetlany komunikat o błędzie. ( [ICLRMetaHost::GetRuntime](../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) — metoda nie akceptuje tej flagi i nie zapewnia inny sposób, aby wyświetlić komunikat o błędzie.)  
  
 System Windows udostępnia [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkID=255242) funkcja, która służy do deklarowania, czy ma komunikaty o błędach, który będzie wyświetlany w wyniku kod, który jest uruchamiany w ramach procesu. Można określić parametr SEM_FAILCRITICALERRORS flagę w celu uniemożliwienia wyświetlania komunikatu o błędzie.  
  
 Jednak w niektórych scenariuszach, należy zastąpić ustawienia parametr SEM_FAILCRITICALERRORS procesu aplikacji. Na przykład jeśli natywnego składnika modelu COM obsługującego środowiska CLR i który znajduje się w procesie, gdzie parametr SEM_FAILCRITICALERRORS ma wartość, można zastąpić flagi, w zależności od wpływu wyświetlanie komunikatów o błędach w ramach tego procesu określonej aplikacji. W takim przypadku można jedną z następujących flag zastąpić parametr SEM_FAILCRITICALERRORS:  
  
-   Użyj METAHOST_POLICY_IGNORE_ERROR_MODE z [ICLRMetaHostPolicy::GetRequestedRuntime](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metody.  
  
-   Użyj RUNTIME_INFO_IGNORE_ERROR_MODE z [GetRequestedRuntimeInfo](../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md) funkcji.  
  
## <a name="ui-policy-for-clr-provided-hosts"></a>Zasady interfejsu użytkownika dla hostów wprowadzone do środowiska CLR  
 CLR zawiera zestaw hostów dla różnych scenariuszy, a te wszystkie hosty wyświetlane komunikaty o błędach, gdy występują problemy podczas ładowania wymagana wersja środowiska uruchomieniowego. Poniższa tabela zawiera listę hostów i ich zasady komunikat błędu.  
  
|Host aparatu CLR|Opis|Błąd komunikatu zasad|Komunikat o błędzie, można wyłączyć?|  
|--------------|-----------------|--------------------------|------------------------------------|  
|Zarządzany host EXE|Powoduje uruchomienie zarządzanych plików exe.|Jest wyświetlany w przypadku brakujących wersja programu .NET Framework|Nie|  
|Zarządzany host COM|Ładunki zarządzane składniki COM do procesu.|Jest wyświetlany w przypadku brakujących wersja programu .NET Framework|Tak, ustawiając parametr SEM_FAILCRITICALERRORS Flaga|  
|ClickOnce host|Uruchamia aplikacji ClickOnce.|Jest wyświetlany w przypadku brakujących wersji programu .NET Framework, począwszy od[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]|Nie|  
|XBAP hosta|Uruchamia aplikacje WPF XBAP.|Jest wyświetlany w przypadku brakujących wersji programu .NET Framework, począwszy od[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]|Nie|  
  
## <a name="includewin8includeswin8-mdmd-behavior-and-ui"></a>[!INCLUDE[win8](../../../includes/win8-md.md)]Zachowanie i interfejsu użytkownika  
 System aktywacji CLR zapewnia te same zachowania i interfejsu użytkownika na [!INCLUDE[win8](../../../includes/win8-md.md)] jak w innych wersjach systemu operacyjnego Windows, chyba że w przypadku napotkania problemów podczas ładowania CLR 2.0. [!INCLUDE[win8](../../../includes/win8-md.md)]zawiera [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], który używa CLR 4.5. Jednak [!INCLUDE[win8](../../../includes/win8-md.md)] nie ma programu .NET Framework 2.0, 3.0 lub 3.5, która Użyj CLR 2.0. W związku z tym aplikacje, które są zależne od CLR 2.0 nie należy uruchamiać na [!INCLUDE[win8](../../../includes/win8-md.md)] domyślnie. Zamiast tego wyświetlane następujące okno dialogowe, aby umożliwić użytkownikom instalowanie programu .NET Framework 3.5. Użytkownicy mogą również włączyć .NET Framework 3.5 w Panelu sterowania. Obie te opcje są omówionych w artykule [zainstalować program .NET Framework 3.5 w systemie Windows 10, Windows 8.1 i Windows 8](../../../docs/framework/install/dotnet-35-windows-10.md).  
  
 ![Okno dialogowe instalacji 3.5 w systemie Windows 8](../../../docs/framework/deployment/media/installdialog.png "installdialog")  
Monituj o instalowanie programu .NET Framework 3.5 na żądanie  
  
> [!NOTE]
>  [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Zastępuje programu .NET Framework 4 (CLR 4) na komputerze użytkownika. W związku z tym aplikacji .NET Framework 4 bezproblemowo, uruchom bez wyświetlania tego okna dialogowego, w [!INCLUDE[win8](../../../includes/win8-md.md)].  
  
 Po zainstalowaniu programu .NET Framework 3.5, użytkownicy mogą uruchamiać aplikacje, które są zależne od programu .NET Framework 2.0, 3.0 lub 3.5 na ich [!INCLUDE[win8](../../../includes/win8-md.md)] komputerów. .NET Framework 1.0 i 1.1 aplikacji, mogą uruchamiać również pod warunkiem, że te aplikacje nie zostały jawnie skonfigurowane do uruchomienia tylko na .NET Framework w wersji 1.0 lub 1.1. Zobacz [Migrowanie z programu .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).  
  
 Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], aby dołączyć wpisy dziennika, służące do rejestrowania, kiedy i dlaczego jest wyświetlany komunikat o błędzie inicjowania została ulepszona rejestrowania aktywacji środowiska CLR. Aby uzyskać więcej informacji, zobacz [porady: debugowanie problemów aktywacji środowiska CLR](../../../docs/framework/deployment/how-to-debug-clr-activation-issues.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik wdrażania dla deweloperów](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 [Instrukcje: Konfiguracja aplikacji do obsługi w programie .NET Framework 4 lub 4.5](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)  
 [Instrukcje: Debugowanie problemów aktywacji środowiska CLR](../../../docs/framework/deployment/how-to-debug-clr-activation-issues.md)  
 [Instalowanie programu .NET Framework 3.5 w systemie Windows 10, Windows 8.1 lub Windows 8](../../../docs/framework/install/dotnet-35-windows-10.md)
