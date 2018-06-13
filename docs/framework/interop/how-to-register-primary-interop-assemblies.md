---
title: 'Porady: rejestrowanie podstawowych zestawów międzyoperacyjnych'
ms.date: 03/30/2017
helpviewer_keywords:
- registering primary interop assemblies
- primary interop assemblies, registering
ms.assetid: 4b2fcf8a-429d-43ce-8334-e026040be8bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f54d77be130d57c39319e81d58ad5af7815e548
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390864"
---
# <a name="how-to-register-primary-interop-assemblies"></a>Porady: rejestrowanie podstawowych zestawów międzyoperacyjnych
Klasy mogą być organizowany tylko przy użyciu współdziałanie z COM i zawsze są przekazywane jako interfejsy. W niektórych przypadkach interfejs używany do organizowania klasy nosi nazwę interfejsu klasy. Aby dowiedzieć się, jak zastępowanie interfejsu klasy przy użyciu interfejsu wybranych przez użytkownika, zobacz [wywoływana otoka COM](../../../docs/framework/interop/com-callable-wrapper.md).  
  
 Mimo że każdy Deweloper, który chce używać typów COM aplikacji .NET Framework, można wygenerować zestawu międzyoperacyjnego, to tworzy tak problem. Zawsze dewelopera importuje i podpisuje Biblioteka typów COM, który developer tworzy zestaw unikatowy typów, które są zgodne z tymi zaimportowane i podpisany przez inny dewelopera. Rozwiązanie tego problemu niezgodności typu jest dla wszystkich deweloperów uzyskanie dostarczonego przez dostawcę i podpisany podstawowego zestawu międzyoperacyjnego.  
  
 Jeśli planujesz ujawniać typów COM innych firm do innych aplikacji, należy zawsze używać podstawowego zestawu międzyoperacyjnego pochodzącymi od tego samego wydawcy jako biblioteki typów, który definiuje. Oprócz zapewnienia zgodności typu gwarantowane, podstawowe zestawy międzyoperacyjne często są dostosowane przez dostawcę do ulepszenia współdziałania.  
  
 Nawet jeśli nie zamierzasz ujawniać typów COM innych firm, przy użyciu podstawowego zestawu międzyoperacyjnego może ułatwić zadanie współdziałanie z COM — składniki. Niemniej jednak ta strategia zawiera nie izolacji od zmiany, jakie typy zdefiniowane w podstawowy zestaw międzyoperacyjny wprowadzać dostawcy. Jeśli aplikacja wymaga takich izolacji, generowanie własnego zestawu międzyoperacyjnego zamiast podstawowego zestawu międzyoperacyjnego.  
  
 Zarejestruj wszystkie nabywane podstawowe zestawy międzyoperacyjne na komputerze deweloperskim przed można odwoływać się je za pomocą [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)]. Visual Studio wyszukuje i używa podstawowego zestawu międzyoperacyjnego odwołania typu z biblioteki typów COM po raz pierwszy. Jeśli program Visual Studio nie może zlokalizować podstawowego zestawu międzyoperacyjnego skojarzone z biblioteki typów, wyświetli monit o jego nabycie lub oferuje zamiast tego utwórz zestawu międzyoperacyjnego. Podobnie [Importer biblioteki typów (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) używa również rejestru można znaleźć podstawowe zestawy międzyoperacyjne.  
  
 Chociaż nie jest konieczne rejestrowanie podstawowych zestawów międzyoperacyjnych, chyba że planujesz używać programu Visual Studio, rejestracja dwie zalety:  
  
-   Zarejestrowany podstawowy zestaw międzyoperacyjny jest jednoznacznie oznaczony w kluczu rejestru oryginalnej biblioteki typów. Rejestracja to najlepszy sposób można zlokalizować podstawowego zestawu międzyoperacyjnego na tym komputerze.  
  
-   Można uniknąć przypadkowego Generowanie i przy użyciu nowego zestawu międzyoperacyjnego, jeśli w czasie w przyszłości, za pomocą programu Visual Studio odwoływać się do typu, dla którego masz wyrejestrować podstawowego zestawu międzyoperacyjnego.  
  
 Użyj [narzędzie rejestracji zestawów (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) zarejestrować podstawowego zestawu międzyoperacyjnego.  
  
### <a name="to-register-a-primary-interop-assembly"></a>Aby zarejestrować podstawowy zestaw międzyoperacyjny  
  
1.  W wierszu polecenia wpisz polecenie:  
  
     **polecenie regasm** *assemblyname*  
  
     W tym poleceniu *assemblyname* to nazwa pliku zestawu, który jest zarejestrowany. Regasm.exe dodaje wpis dla podstawowego zestawu międzyoperacyjnego w kluczu rejestru jako oryginalnego biblioteki typów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rejestruje `CompanyA.UtilLib.dll` podstawowego zestawu międzyoperacyjnego.  
  
```console  
regasm CompanyA.UtilLib.dll  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie za pomocą podstawowe zestawy międzyoperacyjne](https://msdn.microsoft.com/library/306fa1d6-0703-4004-9e93-d0a57f1be81e(v=vs.100))  
 [Lokalizowanie podstawowe zestawy międzyoperacyjne](https://msdn.microsoft.com/library/d6768e4b-cd80-414d-a4f8-05d979eb393b(v=vs.100))  
 [Redystrybuowanie podstawowe zestawy międzyoperacyjne](https://msdn.microsoft.com/library/e76384f0-d631-474c-bdbd-13884cba0265(v=vs.100))
