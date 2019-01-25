---
title: Wdrażanie aplikacji międzyoperacyjnych
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e74e4784d295e46972e10c5b9e1d4cc4bafa944
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496770"
---
# <a name="deploying-an-interop-application"></a>Wdrażanie aplikacji międzyoperacyjnych
Aplikacji międzyoperacyjnych zwykle zawiera zestaw klienta platformy .NET, jeden lub więcej zestawów międzyoperacyjnych reprezentująca różne COM wpisz biblioteki i co najmniej jeden zarejestrowany składników COM. Program Visual Studio i [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] oferuje narzędzia do importowania i Konwertowanie biblioteki typów na zestaw międzyoperacyjny, zgodnie z opisem w [Importowanie biblioteki typów jako zestawu](importing-a-type-library-as-an-assembly.md). Istnieją dwa sposoby wdrażania aplikacji międzyoperacyjnych:  
  
-   Przy użyciu osadzone typy międzyoperacyjne: Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], można nakazać kompilatorowi do osadzenia informacji o typie z zestawu międzyoperacyjnego, w programie wykonywalnym. Kompilator osadza tylko informacje o typie, używanych przez aplikację. Nie masz do wdrożenia zestawu międzyoperacyjnego z aplikacją. Jest to zalecana technika.  
  
-   Przez wdrożenie usług międzyoperacyjnych: Można utworzyć standardowe odwołanie do zestawu międzyoperacyjnego. W tym przypadku zestaw międzyoperacyjny musi zostać wdrożony z aplikacją. Jeśli zostanie zastosowana ta technika, a nie jest używany prywatny składnika modelu COM, zawsze odwoływać się do podstawowego zestawu międzyoperacyjnego (PIA), opublikowana przez autora składnika modelu COM, który chcesz zastosować w kodzie zarządzanym. Aby uzyskać więcej informacji dotyczących tworzenia i używania podstawowych zestawów międzyoperacyjnych, zobacz [podstawowe zestawy międzyoperacyjne](https://msdn.microsoft.com/library/b977a8be-59a0-40a0-a806-b11ffba5c080(v=vs.100)).  
  
 Jeśli używasz osadzone typy międzyoperacyjne, wdrożenie jest niezwykle proste. Nie ma nic specjalnego, należy wykonać. W pozostałej części tego artykułu opisano scenariusze wdrażania usług międzyoperacyjnych z aplikacją.  
  
## <a name="deploying-interop-assemblies"></a>Wdrażanie zestawów międzyoperacyjnych  
 Zespoły mogą mieć silnej nazwy. Zestawu z silną nazwą zawiera klucz publiczny wydawcy, który zapewnia unikatową tożsamość. Zestawy, które są produkowane przez [Importer biblioteki typów (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) mogą być podpisane przez wydawcę za pomocą **/KeyFile** opcji. Zestawy oznaczone można zainstalować w globalnej pamięci podręcznej. Zestawy nieoznaczone musi być zainstalowany na komputerze użytkownika jako zestawy prywatne.  
  
### <a name="private-assemblies"></a>Zestawy prywatne  
 Aby zainstalować zestaw ma być używany przez użytkowników, zarówno plik wykonywalny aplikacji, jak i zestawu międzyoperacyjnego, który zawiera zaimportowane typy modelu COM muszą być zainstalowane w tej samej struktury katalogów. Poniższa ilustracja przedstawia zestaw międzyoperacyjny bez znaku do użycia przez użytkowników Client1.exe i Client2.exe, które znajdują się w katalogach oddzielną aplikację. Zestaw międzyoperacyjny, które jest wywoływane LOANLib.dll w tym przykładzie, jest zainstalowana dwa razy.  
  
 ![Strukturę katalogów oraz ich rejestru Windows](media/comdeployprivate.gif "comdeployprivate")  
Katalog struktury i wpisy rejestru prywatnego wdrożenia  
  
 Wszystkie składniki COM skojarzone z aplikacją, musi być zainstalowany w rejestrze systemu Windows. Jeśli Client1.exe i Client2.exe na ilustracji są zainstalowane na różnych komputerach, należy zarejestrować składników COM na obu komputerach.  
  
### <a name="shared-assemblies"></a>Zestawy udostępnione  
 Zestawy, które są współużytkowane przez wiele aplikacji, należy zainstalować w scentralizowane repozytorium o nazwie w globalnej pamięci podręcznej. Klientów programu .NET można uzyskać dostęp do tej samej kopii zestawu międzyoperacyjnego, który jest podpisany i zainstalowane w globalnej pamięci podręcznej. Aby uzyskać więcej informacji dotyczących tworzenia i używania podstawowych zestawów międzyoperacyjnych, zobacz [podstawowe zestawy międzyoperacyjne](https://msdn.microsoft.com/library/b977a8be-59a0-40a0-a806-b11ffba5c080(v=vs.100)).  
  
## <a name="see-also"></a>Zobacz także
- [Udostępnianie składników COM programowi .NET Framework](exposing-com-components.md)
- [Importowanie biblioteki typów jako zestawu](importing-a-type-library-as-an-assembly.md)
- [Używanie typów modelu COM w kodzie zarządzanym](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))
- [Kompilowanie projektu międzyoperacyjnego](compiling-an-interop-project.md)
