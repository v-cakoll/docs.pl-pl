---
title: 'Instrukcje: Wyłączanie funkcji pomijania silnej nazwy'
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f96ba198a88b10d77509187d0dec9806a9e26b8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155697"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a>Instrukcje: Wyłączanie funkcji pomijania silnej nazwy
Począwszy od wersji programu .NET Framework 3.5 z dodatkiem Service Pack 1 (SP1), podpisy silnej nazwy nie są weryfikowane, gdy zestaw jest ładowany do pełnego zaufania <xref:System.AppDomain> obiektu, takie jak domyślny <xref:System.AppDomain> dla `MyComputer` strefy. Jest to określane jako silnej nazwy pomijania funkcji. W pełni zaufanym środowisku, zażąda dla <xref:System.Security.Permissions.StrongNameIdentityPermission> zawsze kończą się pomyślnie dla podpisanej zestawów pełnego zaufania, niezależnie od ich podpisu. Jedynym ograniczeniem jest to, że zestaw musi być w pełni zaufany, ponieważ jej strefy jest w pełni zaufany. Ponieważ silnej nazwy nie jest czynnikiem decydującym w tych warunkach, nie ma powodu dla niego ma zostać zweryfikowana. Pomijanie sprawdzania poprawności podpisy silnej nazwy oferuje znaczne ulepszenia wydajności.  
  
 Funkcja pomijania ma zastosowanie do dowolnego złożenia pełnego zaufania, który jest nie podpisywane z opóźnieniem i który jest ładowany do dowolnego pełnego zaufania <xref:System.AppDomain> z katalogu określonego przez jego <xref:System.AppDomainSetup.ApplicationBase%2A> właściwości.  
  
 Możesz przesłonić funkcji pomijania dla wszystkich aplikacji na komputerze, ustawiając wartość klucza rejestru. Ustawienie dla pojedynczej aplikacji można zastąpić za pomocą pliku konfiguracji aplikacji. Nie można przywrócić funkcji pomijania dla pojedynczej aplikacji, jeśli została ona wyłączona przy użyciu klucza rejestru.  
  
 Podczas zastąpienia funkcji pomijania silnej nazwy są weryfikowane tylko pod kątem poprawności; nie jest zaznaczone dla <xref:System.Security.Permissions.StrongNameIdentityPermission>. Jeśli chcesz potwierdzić określonej silnej nazwy, musisz wykonać sprawdzanie oddzielnie.  
  
> [!IMPORTANT]
>  Możliwość wymuszenia Weryfikacja silnej nazwy zależy od klucz rejestru zgodnie z opisem w poniższej procedurze. Jeśli aplikacja jest uruchomiona w ramach konta, które nie ma uprawnień listę kontroli dostępu (ACL) kontroli dostępu, dostęp do tego klucza rejestru, to ustawienie jest nieskuteczne. Upewnij się, że prawa listy ACL są skonfigurowane dla tego klucza, aby mogły zostać odczytane dla wszystkich zestawów.  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-all-applications"></a>Aby wyłączyć silnej nazwy pomijania funkcji dla wszystkich aplikacji  
  
-   Na komputerach 32-bitowych w rejestrze systemowym utworzyć wpis typu DWORD o wartości 0, o nazwie `AllowStrongNameBypass` w obszarze HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. Klucz NETFramework.  
  
-   Na komputerach 64-bitowych w rejestrze systemowym utworzyć wpis typu DWORD o wartości 0, o nazwie `AllowStrongNameBypass` w obszarze HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework i HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. Klucze NETFramework.  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-a-single-application"></a>Aby wyłączyć silnej nazwy pomijania funkcji dla pojedynczej aplikacji  
  
1.  Otwórz lub Utwórz plik konfiguracji aplikacji.  
  
     Aby uzyskać więcej informacji na temat tego pliku, zobacz sekcję pliki konfiguracyjne aplikacji w [konfigurowania aplikacji](../../../docs/framework/configure-apps/index.md).  
  
2.  Dodaj następujący wpis:  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 Można przywrócić funkcji pomijania dla aplikacji, usuwając ustawienie pliku konfiguracji lub przez ustawienie atrybutu na wartość "true".  
  
> [!NOTE]
>  Weryfikacja silnej nazwy włączać i wyłączać dla aplikacji, można włączyć tylko wtedy, gdy funkcja pomijania jest włączona na komputerze. Jeśli funkcja pomijania zostało wyłączone dla komputera, silne nazwy są Walidowane dla wszystkich aplikacji i nie można pominąć sprawdzanie poprawności dla pojedynczej aplikacji.  
  
## <a name="see-also"></a>Zobacz także

- [Sn.exe (Narzędzie silnych nazw)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [\<bypassTrustedAppStrongNames> Element](../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [Tworzenie i używanie zestawów o silnej nazwie](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
