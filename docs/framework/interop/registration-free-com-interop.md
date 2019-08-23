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
ms.openlocfilehash: 3134477198f0cd4c821bea456450e98cc73c6ad2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957471"
---
# <a name="registration-free-com-interop"></a>Współdziałanie z modelem COM bez rejestrowania
Niezależna od rejestracji międzyoperacyjność modelu COM aktywuje składnik bez używania rejestru systemu Windows do przechowywania informacji o zestawie. Zamiast rejestrować składnik na komputerze podczas wdrażania, można tworzyć pliki manifestu w stylu Win32 w czasie projektowania, które zawierają informacje o powiązaniu i aktywacji. Te pliki manifestu, a nie klucze rejestru, kierują aktywację obiektu.  
  
 Korzystanie z aktywacji bezpłatnej do rejestracji dla zestawów zamiast rejestrowania ich podczas wdrażania oferuje dwie zalety:  
  
- Można kontrolować, która wersja biblioteki DLL jest aktywowana, gdy na komputerze jest zainstalowana więcej niż jedna wersja.  
  
- Użytkownicy końcowi mogą używać polecenia XCOPY lub FTP do kopiowania aplikacji do odpowiedniego katalogu na komputerze. Aplikację można następnie uruchomić z tego katalogu.  
  
 W tej sekcji opisano dwa typy manifestów, które są zbędne do międzyoperacyjności modelu COM bez rejestracji: manifesty aplikacji i składników. Te manifesty są plikami XML. Manifest aplikacji tworzony przez dewelopera aplikacji zawiera metadane opisujące zestawy i zależności zestawów. Manifest składnika utworzony przez dewelopera składnika zawiera informacje w przeciwnym razie, które znajdują się w rejestrze systemu Windows.  
  
### <a name="requirements-for-registration-free-com-interop"></a>Wymagania dotyczące międzyoperacyjności modelu COM bez rejestracji  
  
1. Obsługa międzyoperacyjności modelu COM bez rejestracji różni się nieco w zależności od typu zestawu biblioteki; w odróżnieniu od tego, czy zestaw jest niezarządzany (COM Side-by-Side) czy zarządzany (. Na podstawie sieci). W poniższej tabeli przedstawiono wymagania dotyczące systemu operacyjnego i wersji .NET Framework dla każdego typu zestawu.  
  
    |Typ zestawu|System operacyjny|Wersja programu .NET Framework|  
    |-------------------|----------------------|----------------------------|  
    |COM obok siebie|Microsoft Windows XP|Nie jest wymagane.|  
    |. Oparte na sieci|Windows XP z dodatkiem SP2|.NET Framework w wersji 1,1 lub nowszej.|  
  
     Rodzina systemów Windows Server 2003 obsługuje również niezależną od rejestracji międzyoperacyjność COM dla programu. Zestawy oparte na sieci.  
  
     Dla. Klasa oparta na sieci, która ma być zgodna z aktywacją niezależną od rejestru z modelu COM, Klasa musi mieć konstruktora bez parametrów i musi być publiczna.  
  
### <a name="configuring-com-components-for-registration-free-activation"></a>Konfigurowanie składników COM do aktywacji bez rejestracji  
  
1. Aby składnik COM mógł uczestniczyć w aktywacji bez rejestracji, musi zostać wdrożony jako zestaw równoległy. Zestawy równoległe są zestawami niezarządzanymi.  Aby uzyskać więcej informacji, zobacz [używanie zestawów równoległych](/windows/desktop/SbsCs/using-side-by-side-assemblies).  
  
     Aby używać zestawów równoległych COM, a. Deweloper aplikacji opartych na sieci musi dostarczyć manifest aplikacji, który zawiera informacje o powiązaniu i aktywacji. Obsługa niezarządzanych zestawów równoległych jest wbudowana w system operacyjny Windows XP. Środowisko uruchomieniowe COM obsługiwane przez system operacyjny skanuje manifest aplikacji w celu uzyskania informacji o aktywacji, gdy aktywowany składnik nie znajduje się w rejestrze.  
  
     Aktywacja bez rejestracji jest opcjonalna dla składników COM zainstalowanych w systemie Windows XP. Aby uzyskać szczegółowe instrukcje dotyczące dodawania zestawu równoległego do aplikacji, zobacz [używanie zestawów równoległych](/windows/desktop/SbsCs/using-side-by-side-assemblies).  
  
    > [!NOTE]
    > Wykonywanie równoczesne jest funkcją .NET Framework, która umożliwia obsługę wielu wersji środowiska uruchomieniowego oraz wielu wersji aplikacji i składników, które używają wersji środowiska uruchomieniowego, do uruchamiania na tym samym komputerze w tym samym czasie. Wykonywanie równoczesne i zestawy równoległe są różnymi mechanizmami zapewniania funkcji równoległych.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Konfigurowanie składników COM opartych na .NET Framework na potrzeby aktywacji bez rejestracji](../../../docs/framework/interop/configure-net-framework-based-com-components-for-reg.md)
