---
title: 'Instrukcje: wyłączanie funkcji pomijania silnej nazwy'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
ms.openlocfilehash: a4c4ae7ea61a659d3bede532da3c1bdaea448873
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141105"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a>Instrukcje: wyłączanie funkcji pomijania silnej nazwy
Począwszy od wersji 3,5 .NET Framework programu Service Pack 1 (SP1), sygnatury silnej nazwy nie są sprawdzane, gdy zestaw jest ładowany do obiektu <xref:System.AppDomain> pełnego zaufania, takiego jak domyślny <xref:System.AppDomain> dla strefy `MyComputer`. Jest to nazywane funkcją pomijania silnej nazwy. W środowisku pełnego zaufania wymagania dotyczące <xref:System.Security.Permissions.StrongNameIdentityPermission> zawsze powiodło się dla podpisanych, pełnych zestawów, niezależnie od ich sygnatur. Jedynym ograniczeniem jest to, że zestaw musi być w pełni zaufany, ponieważ jego strefa jest w pełni zaufana. Ponieważ silna nazwa nie jest czynnikiem decydującym w tych warunkach, nie ma powodów, dla których nie można jej zweryfikować. Pomijanie sprawdzania poprawności sygnatur silnych nazw zapewnia znaczną poprawę wydajności.  
  
 Funkcja Bypass ma zastosowanie do dowolnego zestawu pełnego zaufania, który nie jest podpisany z opóźnieniem i który jest ładowany do dowolnego <xref:System.AppDomain> pełnego zaufania z katalogu określonego przez jego właściwość <xref:System.AppDomainSetup.ApplicationBase%2A>.  
  
 Można zastąpić funkcję pomijania dla wszystkich aplikacji na komputerze przez ustawienie wartości klucza rejestru. Można zastąpić ustawienie pojedynczej aplikacji przy użyciu pliku konfiguracyjnego aplikacji. Nie można przywrócić funkcji pomijania dla pojedynczej aplikacji, jeśli została ona wyłączona przez klucz rejestru.  
  
 Gdy zastąpisz funkcję pomijania, silna nazwa jest weryfikowana tylko pod kątem poprawności; nie jest ona sprawdzana dla <xref:System.Security.Permissions.StrongNameIdentityPermission>. Jeśli chcesz potwierdzić konkretną silną nazwę, musisz wykonać to sprawdzenie oddzielnie.  
  
> [!IMPORTANT]
> Możliwość wymuszenia weryfikacji silnej nazwy zależy od klucza rejestru, zgodnie z opisem w poniższej procedurze. Jeśli aplikacja jest uruchomiona w ramach konta, które nie ma uprawnień do uzyskiwania dostępu do tego klucza rejestru na liście kontroli dostępu (ACL), to ustawienie jest nieskuteczne. Musisz się upewnić, że dla tego klucza są skonfigurowane uprawnienia ACL, aby można było je odczytać dla wszystkich zestawów.  
  
## <a name="disable-the-strong-name-bypass-feature-for-all-applications"></a>Wyłącz funkcję pomijania silnej nazwy dla wszystkich aplikacji  
  
- Na komputerach 32-bitowych w rejestrze systemu Utwórz wpis DWORD o wartości 0 o nazwie `AllowStrongNameBypass` w ramach\\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft. Klucz NETFramework.  
  
- Na komputerach 64-bitowych w rejestrze systemu Utwórz wpis DWORD o wartości 0 o nazwie `AllowStrongNameBypass` w ramach\\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft. NETFramework i HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. Klucze NETFramework.  
  
## <a name="disable-the-strong-name-bypass-feature-for-a-single-application"></a>Wyłączenie funkcji pomijania silnej nazwy dla pojedynczej aplikacji  
  
1. Otwórz lub Utwórz plik konfiguracji aplikacji.  
  
    Aby uzyskać więcej informacji na temat tego pliku, zapoznaj się z sekcją pliki konfiguracyjne aplikacji w artykule [Konfigurowanie aplikacji](../../framework/configure-apps/index.md).  
  
2. Dodaj następujący wpis:  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 Można przywrócić funkcję pomijania dla aplikacji przez usunięcie ustawienia pliku konfiguracji lub przez ustawienie atrybutu na `true`.  
  
> [!NOTE]
> Można włączać i wyłączać sprawdzanie silnej nazwy dla aplikacji tylko wtedy, gdy Funkcja pomijania jest włączona dla komputera. Jeśli funkcja pomijania została wyłączona dla komputera, silne nazwy są weryfikowane dla wszystkich aplikacji i nie można pominąć walidacji dla pojedynczej aplikacji.  
  
## <a name="see-also"></a>Zobacz także

- [Sn.exe (narzędzie silnych nazw)](../../framework/tools/sn-exe-strong-name-tool.md)
- [\<element > bypassTrustedAppStrongNames](../../framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [Tworzenie i używanie zestawów o silnych nazwach](create-use-strong-named.md)
