---
title: 'Jak: Wyłącz funkcję pomijania silnej nazwy'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
ms.openlocfilehash: a4c4ae7ea61a659d3bede532da3c1bdaea448873
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141105"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a>Jak: Wyłącz funkcję pomijania silnej nazwy
Począwszy od .NET Framework w wersji 3.5 z dodatkiem Service Pack 1 (SP1), podpisy <xref:System.AppDomain> o silnej nazwie <xref:System.AppDomain> nie `MyComputer` są weryfikowane po załadowaniu zestawu do obiektu pełnego zaufania, takiego jak domyślna dla strefy. Jest to określane jako funkcja pomijania silnej nazwy. W środowisku pełnego zaufania wymagania <xref:System.Security.Permissions.StrongNameIdentityPermission> dotyczące zawsze odnoszą sukcesy dla podpisanych zestawów o pełnym zaufaniu, niezależnie od ich podpisu. Jedynym ograniczeniem jest to, że zestaw musi być w pełni zaufany, ponieważ jego strefa jest w pełni zaufana. Ponieważ silna nazwa nie jest czynnikiem decydującym w tych warunkach, nie ma powodu, aby zostać zweryfikowane. Pomijanie sprawdzania poprawności podpisów o silnej nazwie zapewnia znaczną poprawę wydajności.  
  
 Funkcja pomijania ma zastosowanie do każdego zestawu pełnego zaufania, który nie jest podpisany <xref:System.AppDomain> z opóźnieniem i <xref:System.AppDomainSetup.ApplicationBase%2A> który jest ładowany do dowolnego pełnego zaufania z katalogu określonego przez jego właściwość.  
  
 Funkcję pomijania dla wszystkich aplikacji na komputerze można zastąpić, ustawiając wartość klucza rejestru. Można zastąpić ustawienie dla pojedynczej aplikacji przy użyciu pliku konfiguracji aplikacji. Nie można przywrócić funkcji pomijania dla pojedynczej aplikacji, jeśli została ona wyłączona przez klucz rejestru.  
  
 Po zastąpieniu funkcji pomijania silna nazwa jest sprawdzana tylko pod kątem poprawności; nie jest sprawdzany <xref:System.Security.Permissions.StrongNameIdentityPermission>pod kątem . Jeśli chcesz potwierdzić określoną silną nazwę, musisz wykonać tę kontrolę oddzielnie.  
  
> [!IMPORTANT]
> Możliwość wymuszenia sprawdzania poprawności silnej nazwy zależy od klucza rejestru, zgodnie z opisem w poniższej procedurze. Jeśli aplikacja jest uruchomiona na koncie, które nie ma uprawnień listy kontroli dostępu (ACL) do dostępu do tego klucza rejestru, ustawienie jest nieskuteczne. Należy upewnić się, że prawa acl są skonfigurowane dla tego klucza, dzięki czemu mogą być odczytywane dla wszystkich zestawów.  
  
## <a name="disable-the-strong-name-bypass-feature-for-all-applications"></a>Wyłącz funkcję pomijania silnej nazwy dla wszystkich aplikacji  
  
- Na komputerach 32-bitowych w rejestrze systemowym utwórz wpis `AllowStrongNameBypass` DWORD o wartości\\0 o nazwie pod HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft . NETFramework.  
  
- Na komputerach 64-bitowych w rejestrze systemowym utwórz wpis `AllowStrongNameBypass` DWORD o wartości\\0 o nazwie pod HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft . NETFramework i HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Węzeł\Microsoft\\. NETFramework.  
  
## <a name="disable-the-strong-name-bypass-feature-for-a-single-application"></a>Wyłączanie funkcji pomijania silnej nazwy dla pojedynczej aplikacji  
  
1. Otwórz lub utwórz plik konfiguracyjny aplikacji.  
  
    Aby uzyskać więcej informacji na temat tego pliku, zobacz sekcję Pliki konfiguracji aplikacji w [polu Konfigurowanie aplikacji](../../framework/configure-apps/index.md).  
  
2. Dodaj następujący wpis:  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 Funkcję pomijania aplikacji można przywrócić, usuwając ustawienie pliku konfiguracyjnego `true`lub ustawiając atrybut na .  
  
> [!NOTE]
> Sprawdzanie poprawności silnej nazwy można włączać i wyłączać dla aplikacji tylko wtedy, gdy funkcja pomijania jest włączona dla komputera. Jeśli funkcja pomijania została wyłączona dla komputera, silne nazwy są sprawdzane dla wszystkich aplikacji i nie można obejść sprawdzania poprawności dla pojedynczej aplikacji.  
  
## <a name="see-also"></a>Zobacz też

- [Sn.exe (Narzędzie silnych nazw)](../../framework/tools/sn-exe-strong-name-tool.md)
- [\<obejśćTrustedAppStrongNames> element](../../framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [Tworzenie i używanie zestawów o silnej nazwie](create-use-strong-named.md)
