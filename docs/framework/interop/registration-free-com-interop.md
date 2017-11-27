---
title: "Współdziałanie z modelem COM bez rejestrowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], interop
- COM interop, registration-free COM interop
- registration-free COM interop
- manifests [.NET Framework]
- registration-free activation
- object activation
- registration-free COM interop, about registration-free COM interop
ms.assetid: 90f308b9-82dc-414a-bce1-77e0155e56bd
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 28ecb3419bddcc8e9a192b240a7bf90474314c1f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="registration-free-com-interop"></a>Współdziałanie z modelem COM bez rejestrowania
Współdziałanie z COM bez rejestrowania aktywuje składnika bez za pomocą rejestru systemu Windows do przechowywania informacji o zestawie. Zamiast zarejestrować składników na komputerze podczas wdrażania, można tworzyć pliki manifestu Win32 stylu w czasie projektowania, zawierających informacje o powiązaniu i aktywacji. Te pliki manifestu, zamiast klucze rejestru, bezpośrednie aktywacji obiektu.  
  
 Przy użyciu aktywacji bez rejestracji dla ponownie zestawy zamiast zarejestrować ich podczas wdrażania oferuje dwie zalety:  
  
-   Można kontrolować, która wersja biblioteki DLL jest aktywowany, gdy więcej niż jedna wersja jest zainstalowany na komputerze.  
  
-   Umożliwia użytkownikom XCOPY lub FTP można skopiować aplikacji do odpowiedniego katalogu na swoim komputerze. Aplikacja może następnie uruchamiana z tego katalogu.  
  
 W tej sekcji opisano dwa typy manifestów potrzebne do międzyoperacyjności z modelem COM bez rejestrowania: manifestów aplikacji i składnika. Te manifesty są plikami XML. Manifest aplikacji, który jest tworzony przez dewelopera aplikacji, zawiera metadane opisujące zestawów i zależności zestawu. Manifestu składnika, utworzonych przez dewelopera składnika zawiera informacje, w przeciwnym razie znajduje się w rejestrze systemu Windows.  
  
### <a name="requirements-for-registration-free-com-interop"></a>Wymagania dotyczące współdziałanie z COM bez rejestrowania  
  
1.  Obsługa współdziałanie z COM bez rejestrowania różni się nieco w zależności od typu biblioteki zestawu; w szczególności czy zestaw jest niezarządzane (COM side-by-side) lub zarządzanych (. NET-based). W poniższej tabeli przedstawiono wymagania dotyczące wersji .NET Framework dla każdego typu zestawu i system operacyjny.  
  
    |Typ zestawu|System operacyjny|Wersja programu .NET Framework|  
    |-------------------|----------------------|----------------------------|  
    |COM side-by-side|Microsoft Windows XP|Nie jest wymagane.|  
    |. Na podstawie NET|Windows XP z dodatkiem SP2|NET Framework w wersji 1.1 lub nowszej.|  
  
     System Windows Server 2003 obsługuje również współdziałanie COM bez rejestrowania dla. Zestawy opartych na sieci.  
  
     Aby uzyskać. Oparte na sieci klasy, aby był zgodny z rejestru bez aktywacji z modelu COM, klasa musi mieć konstruktora domyślnego i muszą być publiczne.  
  
### <a name="configuring-com-components-for-registration-free-activation"></a>Konfigurowanie aktywacji bez rejestracji składników COM  
  
1.  Dla składnika modelu COM o uczestnictwie w aktywacji bez rejestracji musi być wdrożony jako zestawu side-by-side. Zestawy Side-by-side są niezarządzane zestawów.  Aby uzyskać więcej informacji, zobacz [używanie zestawów Side-by-side](https://msdn.microsoft.com/library/windows/desktop/aa376618.aspx).  
  
     Używanie zestawów side-by-side COM,. Deweloper aplikacji opartych na sieci należy podać manifest aplikacji, który zawiera informacje o powiązaniu i aktywacji. Obsługa niezarządzane zestawy side-by-side jest wbudowane w system operacyjny Windows XP. COM środowiska uruchomieniowego, obsługiwane przez system operacyjny skanuje manifest aplikacji, aby uzyskać informacje dotyczące aktywacji, gdy składnik aktywowane nie jest w rejestrze.  
  
     Aktywacja bez rejestrowania jest opcjonalne dla składników modelu COM w systemie Windows XP. Aby uzyskać szczegółowe instrukcje dotyczące dodawania zestawu side-by-side do aplikacji, zobacz [używanie zestawów Side-by-side](https://msdn.microsoft.com/library/windows/desktop/aa376618.aspx).  
  
    > [!NOTE]
    >  Wykonanie Side-by-side jest funkcja .NET Framework, która umożliwia wielu wersji środowiska uruchomieniowego i wiele wersji aplikacji i składników, których używana jest wersja środowiska uruchomieniowego, do uruchamiania na tym samym komputerze, w tym samym czasie. Wykonanie Side-by-side i zestawy side-by-side są różne mechanizmy dostarczanie side-by-side funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Konfigurowanie aktywacji bez rejestracji składników COM opartych na Framework .NET](../../../docs/framework/interop/configure-net-framework-based-com-components-for-reg.md)
