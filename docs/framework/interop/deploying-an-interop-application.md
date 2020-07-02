---
title: Wdrażanie aplikacji międzyoperacyjnych
description: Wdróż aplikację międzyoperacyjną, która zazwyczaj ma zestaw klienta platformy .NET, zestawy międzyoperacyjności różnych bibliotek typów COM oraz zarejestrowane składniki COM.
ms.date: 03/30/2017
helpviewer_keywords:
- deploying applications [.NET Framework], interop
- strong-named assemblies, interop applications
- unsigned assemblies
- private assemblies
- exposing COM components to .NET Framework
- interoperation with unmanaged code, deploying applications
- shared assemblies
- COM interop, deploying applications
- interoperation with unmanaged code, exposing COM components
- signed assemblies
- COM interop, exposing COM components
ms.assetid: ea8a403e-ae03-4faa-9d9b-02179ec72992
ms.openlocfilehash: 744307d4175d151d07acbedd5815e538307c8973
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617486"
---
# <a name="deploying-an-interop-application"></a>Wdrażanie aplikacji międzyoperacyjnych
Aplikacja międzyoperacyjna zwykle zawiera zestaw klienta .NET, co najmniej jeden zestaw międzyoperacyjny reprezentujący różne biblioteki typów COM oraz co najmniej jeden zarejestrowany składnik COM. Program Visual Studio i Windows SDK udostępniają narzędzia do importowania i konwersji biblioteki typów na zestaw międzyoperacyjny, jak opisano w [importowania biblioteki typów jako zestawu](importing-a-type-library-as-an-assembly.md). Istnieją dwa sposoby wdrożenia aplikacji międzyoperacyjnego:  
  
- Korzystając z osadzonych typów międzyoperacyjnych: począwszy od .NET Framework 4, można wydać kompilatorowi, aby osadzi informacje o typie z zestawu międzyoperacyjnego do pliku wykonywalnego. Kompilator osadza tylko informacje o typie używane przez aplikację. Nie trzeba wdrażać zestawu międzyoperacyjnego przy użyciu aplikacji. Jest to zalecana technika.  
  
- Przez wdrożenie zestawów międzyoperacyjnych: można utworzyć standardowe odwołanie do zestawu międzyoperacyjnego. W takim przypadku zestaw międzyoperacyjny musi zostać wdrożony wraz z aplikacją. Jeśli ta technika jest stosowana i nie używasz prywatnego składnika COM, zawsze odwołuje się do podstawowego zestawu międzyoperacyjnego (PIA) opublikowanego przez autora składnika COM, który ma zostać dołączony do kodu zarządzanego. Aby uzyskać więcej informacji na temat tworzenia i używania podstawowych zestawów międzyoperacyjnych, zobacz [podstawowe zestawy międzyoperacyjności](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).  
  
 W przypadku korzystania z osadzonych typów międzyoperacyjnych wdrożenie jest proste i proste. Nie ma żadnych specjalnych, które należy wykonać. W dalszej części tego artykułu opisano scenariusze wdrażania zestawów międzyoperacyjnych w aplikacji.  
  
## <a name="deploying-interop-assemblies"></a>Wdrażanie zestawów międzyoperacyjnych  
 Zestawy mogą mieć silne nazwy. Zestaw o silnej nazwie zawiera klucz publiczny wydawcy, który zapewnia unikatową tożsamość. Zestawy, które są tworzone przez [importera biblioteki typów (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) , mogą być podpisane przez wydawcę przy użyciu opcji **/KeyFile** . Można zainstalować podpisane zestawy w globalnej pamięci podręcznej zestawów. Zestawy bez znaku muszą być zainstalowane na komputerze użytkownika jako prywatne zespoły.  
  
### <a name="private-assemblies"></a>Zestawy prywatne  
 Aby zainstalować zestaw, który ma być używany prywatnie, należy zainstalować zarówno plik wykonywalny aplikacji, jak i zestaw międzyoperacyjny zawierający zaimportowane typy COM w tej samej strukturze katalogów. Na poniższej ilustracji przedstawiono niepodpisany zestaw międzyoperacyjny, który ma być używany prywatnie przez Client1.exe i Client2.exe, które znajdują się w oddzielnych katalogach aplikacji. Zestaw międzyoperacyjny, który jest nazywany LOANLib.dll w tym przykładzie, jest instalowany dwa razy.  
  
 ![Struktura katalogów i rejestr systemu Windows](./media/deploying-an-interop-application/com-private-deployment.gif "Struktura katalogów i wpisy rejestru dla prywatnego wdrożenia")  
  
 Wszystkie składniki COM skojarzone z aplikacją muszą być zainstalowane w rejestrze systemu Windows. Jeśli Client1.exe i Client2.exe na ilustracji są zainstalowane na różnych komputerach, należy zarejestrować składniki COM na obu komputerach.  
  
### <a name="shared-assemblies"></a>Zestawy udostępnione  
 Zestawy, które są współużytkowane przez wiele aplikacji, powinny być zainstalowane w scentralizowanym repozytorium o nazwie globalna pamięć podręczna zestawów. Klienci platformy .NET mogą uzyskać dostęp do tej samej kopii zestawu międzyoperacyjnego, który jest podpisany i zainstalowany w globalnej pamięci podręcznej zestawów. Aby uzyskać więcej informacji na temat tworzenia i używania podstawowych zestawów międzyoperacyjnych, zobacz [podstawowe zestawy międzyoperacyjności](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).  
  
## <a name="see-also"></a>Zobacz także

- [Udostępnianie składników COM programowi.NET Framework](exposing-com-components.md)
- [Importowanie biblioteki typów jako zestawu](importing-a-type-library-as-an-assembly.md)
- [Używanie typów COM w kodzie zarządzanym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Kompilowanie projektu międzyoperacyjnego](compiling-an-interop-project.md)
