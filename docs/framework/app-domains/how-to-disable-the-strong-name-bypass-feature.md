---
title: 'Porady: wyłączanie funkcji pomijania silnej nazwy'
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9604969ea073b07af0eca8d481f5459ee15d099
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742422"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a>Porady: wyłączanie funkcji pomijania silnej nazwy
Począwszy od wersji programu .NET Framework 3.5 z dodatkiem Service Pack 1 (SP1), podpisów silnej nazwy nie są weryfikowane podczas zestaw jest ładowany do pełnego zaufania <xref:System.AppDomain> obiektu, takie jak domyślny <xref:System.AppDomain> dla `MyComputer` strefy. Jest to określane jako silnej nazwy pomijania funkcji. W pełni zaufanym środowisku, wymaga dla <xref:System.Security.Permissions.StrongNameIdentityPermission> zawsze powiodła się dla podpisanej zestawy pełnego zaufania, niezależnie od ich podpisu. Tylko ograniczenie jest, że zestaw muszą być całkowicie zaufane, ponieważ jej strefy jest w pełni zaufany. Silna nazwa nie jest czynnikiem decydującym w tych warunkach, nie istnieje przyczyna jej do sprawdzenia poprawności. Pomijanie sprawdzania poprawności podpisów silnej nazwy zapewnia znaczną poprawę wydajności.  
  
 Funkcja pomijania dotyczy dowolnego zestawu pełnego zaufania, który jest nie podpisywany z opóźnieniem i który jest ładowany do dowolnego pełnego zaufania <xref:System.AppDomain> z katalogu określonego przez jego <xref:System.AppDomainSetup.ApplicationBase%2A> właściwości.  
  
 Funkcja pomijania dla wszystkich aplikacji na komputerze można zmienić, ustawiając wartość klucza rejestru. Można zastąpić to ustawienie dla jednej aplikacji przy użyciu pliku konfiguracji aplikacji. Nie można przywrócić funkcja pomijania dla jednej aplikacji, jeśli wyłączono go przy użyciu klucza rejestru.  
  
 Gdy przesłonięcia funkcji pomijania silnej nazwy jest weryfikowane tylko pod kątem poprawności; nie jest zaznaczone dla <xref:System.Security.Permissions.StrongNameIdentityPermission>. Aby potwierdzić określonych silnej nazwy, należy wykonać sprawdzanie oddzielnie.  
  
> [!IMPORTANT]
>  Możliwość wymuszenia Walidacja silnej nazwy jest zależna od klucz rejestru zgodnie z opisem w poniższej procedurze. Jeśli aplikacja działa w ramach konta, które nie ma dostępu do kontroli listę kontroli dostępu (ACL) uprawnienia dostępu do tego klucza rejestru, to ustawienie jest nieskuteczne. Upewnij się czy praw listy ACL są skonfigurowane dla tego klucza, dzięki czemu mogą być odczytywane dla wszystkich zestawów.  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-all-applications"></a>Aby wyłączyć silnej nazwy pomijania funkcji dla wszystkich aplikacji  
  
-   Na komputerach z 32-bitowe w rejestrze systemu utworzyć wpis DWORD o wartości 0 o nazwie `AllowStrongNameBypass` w obszarze HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. Klucz NETFramework.  
  
-   Na komputerach 64-bitowych w rejestrze systemu, Utwórz wpis DWORD o wartości 0 o nazwie `AllowStrongNameBypass` w obszarze HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework i HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. Klucze NETFramework.  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-a-single-application"></a>Aby wyłączyć silnej nazwy pomijania funkcji dla jednej aplikacji  
  
1.  Otwarcia lub utworzenia pliku konfiguracji aplikacji.  
  
     Aby uzyskać więcej informacji na temat tego pliku, zobacz sekcję pliki konfiguracji aplikacji w [konfigurowania aplikacji](../../../docs/framework/configure-apps/index.md).  
  
2.  Dodaj następujący wpis:  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 Funkcja pomijania dla aplikacji można przywrócić przez usunięcie ustawienie pliku konfiguracji lub ustawienie atrybutu na wartość "true".  
  
> [!NOTE]
>  Walidacja silnej nazwy włączać i wyłączać dla aplikacji można włączyć tylko wtedy, gdy funkcja pomijania jest włączona na komputerze. Jeśli funkcja pomijania zostało wyłączone dla komputera, silnych nazw są weryfikowane dla wszystkich aplikacji i nie można pominąć weryfikacji dla pojedynczej aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Sn.exe (narzędzie silnych nazw)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 [\<bypasstrustedappstrongnames — > — Element](../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)  
 [Tworzenie i używanie zestawów o silnej nazwie](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
