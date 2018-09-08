---
title: Współdziałanie z modelem COM bez rejestrowania
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], interop
- COM interop, registration-free COM interop
- registration-free COM interop
- manifests [.NET Framework]
- registration-free activation
- object activation
- registration-free COM interop, about registration-free COM interop
ms.assetid: 90f308b9-82dc-414a-bce1-77e0155e56bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 939630726f399184c264f73ee01270f50981e83a
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44209111"
---
# <a name="registration-free-com-interop"></a>Współdziałanie z modelem COM bez rejestrowania
Współdziałanie COM interop aktywuje składnika bez za pomocą rejestru Windows do przechowywania informacji o zestawie. Zamiast rejestrowanie składników na komputerze podczas wdrażania, utworzysz plik manifestu Win32 stylu w czasie projektowania, które zawierają informacje dotyczące powiązania i aktywacji. Te pliki manifestu, zamiast kluczy rejestru, bezpośrednie aktywacji obiektu.  
  
 Przy użyciu aktywacji bez rejestracji dla zestawów zamiast rejestrowania ich podczas wdrażania ma dwie zalety:  
  
-   Można kontrolować, którą wersję biblioteki DLL jest aktywowany, gdy więcej niż jedna wersja jest zainstalowana na komputerze.  
  
-   Użytkownicy końcowi można użyć polecenia XCOPY lub FTP można skopiować aplikacji do odpowiedniego katalogu na komputerze. Aplikacja może następnie uruchamiana z tego katalogu.  
  
 W tej sekcji opisano dwa typy służące do współdziałania z modelem COM bez rejestrowania manifesty: manifestów aplikacji i składników. Te manifesty są plikami XML. Manifest aplikacji, który jest tworzony przez dewelopera aplikacji, zawiera metadane opisujące zestawów i zależności zestawu. Manifestu składnika, utworzonych przez dewelopera składnik zawiera informacje, w przeciwnym razie znajduje się w rejestrze systemu Windows.  
  
### <a name="requirements-for-registration-free-com-interop"></a>Wymagania dotyczące współdziałania z modelem COM bez rejestrowania  
  
1.  Obsługa rejestracji wolnego modelu COM interop różni się nieco w zależności od typu biblioteki zestawu; w szczególności zestaw niezarządzanych (COM side-by-side) czy jest zarządzany (. NET-based). W poniższej tabeli przedstawiono systemu operacyjnego i wymagania dotyczące wersji .NET Framework dla każdego typu zestawu.  
  
    |Typ zestawu|System operacyjny|Wersja programu .NET Framework|  
    |-------------------|----------------------|----------------------------|  
    |COM side-by-side|Microsoft Windows XP|Nie jest wymagane.|  
    |. Na podstawie NET|Windows XP z dodatkiem SP2|NET Framework w wersji 1.1 lub nowszej.|  
  
     W systemach z rodziny Windows Server 2003 obsługuje również bez rejestracji usługa międzyoperacyjna modelu COM dla. Zestawy oparte na sieci.  
  
     Aby uzyskać. Na podstawie NET klasy, aby był zgodny z bezpłatnych rejestru aktywacji z modelu COM, klasa musi mieć konstruktora domyślnego i muszą być publiczne.  
  
### <a name="configuring-com-components-for-registration-free-activation"></a>Konfigurowanie aktywacji bez rejestracji składników COM  
  
1.  Dla składnika modelu COM do wzięcia udziału w aktywacji bez rejestracji musi zostać wdrożony jako zestawu side-by-side. Side-by-side zestawy są niezarządzane zestawów.  Aby uzyskać więcej informacji, zobacz [używanie zestawów Side-by-side](/windows/desktop/SbsCs/using-side-by-side-assemblies).  
  
     Używanie zestawów side-by-side COM,. Deweloper aplikacji opartych na sieci należy podać manifest aplikacji, który zawiera informacje dotyczące powiązania i aktywacji. Obsługa dla niezarządzanych zestawów side-by-side jest wbudowana w system operacyjny Windows XP. Środowisko uruchomieniowe modelu COM, obsługiwana przez system operacyjny skanuje manifest aplikacji, aby uzyskać informacje o aktywacji, gdy składnik aktywowanego nie znajduje się w rejestrze.  
  
     Aktywacji bez rejestracji jest opcjonalne dla składników COM, w systemie Windows XP. Aby uzyskać szczegółowe instrukcje na temat dodawania zestawów side-by-side do aplikacji, zobacz [używanie zestawów Side-by-side](/windows/desktop/SbsCs/using-side-by-side-assemblies).  
  
    > [!NOTE]
    >  Wykonanie Side-by-side jest funkcja .NET Framework, która umożliwia wielu wersji środowiska uruchomieniowego i wiele wersji aplikacji i składników, korzystających z wersji środowiska uruchomieniowego, aby uruchomić na tym samym komputerze, w tym samym czasie. Wykonanie Side-by-side i zestawów side-by-side są różne mechanizmy dostarczanie funkcji side-by-side.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Konfigurowanie aktywacji bez rejestracji składników COM opartych na platformie .NET Framework](../../../docs/framework/interop/configure-net-framework-based-com-components-for-reg.md)
