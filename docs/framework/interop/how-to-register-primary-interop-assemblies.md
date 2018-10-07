---
title: 'Porady: rejestrowanie podstawowych zestawów międzyoperacyjnych'
ms.date: 03/30/2017
helpviewer_keywords:
- registering primary interop assemblies
- primary interop assemblies, registering
ms.assetid: 4b2fcf8a-429d-43ce-8334-e026040be8bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9017e8dc50914bbffbcea52192e6ec10fbc7a6df
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48840824"
---
# <a name="how-to-register-primary-interop-assemblies"></a>Porady: rejestrowanie podstawowych zestawów międzyoperacyjnych

Klasy mogą być organizowane wyłącznie przez współdziałania z modelem COM i zawsze są przekazywane jako interfejsy. W niektórych przypadkach interfejs używany do organizowania klasy jest nazywane interfejsu klasy. Aby dowiedzieć się, jak zastępowanie interfejsu klasy za pomocą ulubionego interfejsu, zobacz [wywoływana otoka COM](../../../docs/framework/interop/com-callable-wrapper.md).

 Mimo że każdy Deweloper, który chce użyć typów modelu COM z poziomu aplikacji .NET Framework może generować zestaw międzyoperacyjny, wykonanie tej tak więc tworzy problem. Każdorazowo Deweloper importuje i rejestruje bibliotekę typów modelu COM, deweloper tworzy zestaw unikatowe typy, które są zgodne z tymi zaimportowane i podpisany przez inny dla deweloperów. To rozwiązanie tego problemu niezgodności typu dla każdego dewelopera uzyskać dostarczonego przez dostawcę i podpisany podstawowego zestawu międzyoperacyjnego.

 Jeśli planujesz ujawniać innych typów modelu COM do innych aplikacji, należy zawsze używać podstawowy zestaw międzyoperacyjny dostarczonych przez tego samego wydawcy, jak biblioteka typów, które definiuje. Ponadto, aby zapewnić zgodność z typem gwarantowane, podstawowe zestawy międzyoperacyjne często są dostosowywane przez dostawcę do ulepszenia współdziałania.

 Nawet jeśli nie planujesz udostępnianie innych typów modelu COM, zadanie współdziałanie ze składnikami modelu COM. może ułatwić przy użyciu podstawowego zestawu międzyoperacyjnego. Jednak ta strategia zapewnia nie izolacji od zmian, jakie typy zdefiniowane w podstawowy zestaw międzyoperacyjny wprowadzać dostawcy. Gdy aplikacja wymaga takich izolacji, generowanie własnego zestawu międzyoperacyjnego, zamiast korzystać z podstawowego zestawu międzyoperacyjnego.

 Można się odwołać je za pomocą programu Visual Studio na komputerze deweloperskim należy zarejestrować wszystkie uzyskano podstawowe zestawy międzyoperacyjne. Visual Studio szuka i używa podstawowego zestawu międzyoperacyjnego, możesz odwołać się do typu z biblioteki typów COM po raz pierwszy. Jeśli program Visual Studio nie może zlokalizować podstawowego zestawu międzyoperacyjnego skojarzone z biblioteki typów, monituje o je nabyć lub oferuje zamiast tego utwórz zestaw międzyoperacyjny. Podobnie [Importer biblioteki typów (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) również używa rejestru do zlokalizowania podstawowe zestawy międzyoperacyjne.

 Chociaż nie jest to konieczne zarejestrować podstawowe zestawy międzyoperacyjne, chyba że zamierzasz używać programu Visual Studio, rejestracji ma dwie zalety:

-   Zarejestrowanego podstawowego zestawu międzyoperacyjnego jest jednoznacznie oznaczony w kluczu rejestru oryginalnej biblioteki typów. Rejestracja jest najlepszym sposobem lokalizowania podstawowego zestawu międzyoperacyjnego na tym komputerze.

-   Możesz uniknąć przypadkowego generowania i za pomocą nowego zestawu międzyoperacyjnego, jeśli w czasie w przyszłości, należy używać programu Visual Studio, aby odwołać się do typu, dla którego ma się wyrejestrować podstawowy zestaw międzyoperacyjny.

Użyj [narzędzie rejestracji zestawów (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) zarejestrować podstawowy zestaw międzyoperacyjny.

## <a name="to-register-a-primary-interop-assembly"></a>Aby zarejestrować się podstawowy zestaw międzyoperacyjny

1.  W wierszu polecenia wpisz polecenie:

     **regasm** *assemblyname*

     W tym poleceniu *assemblyname* jest nazwą pliku zestawu, który jest zarejestrowany. Regasm.exe dodaje wpis dla podstawowego zestawu międzyoperacyjnego w kluczu rejestru jako oryginalnej biblioteki typów.

## <a name="example"></a>Przykład
 Poniższy przykład rejestruje `CompanyA.UtilLib.dll` podstawowy zestaw międzyoperacyjny.

```console
regasm CompanyA.UtilLib.dll
```

## <a name="see-also"></a>Zobacz też

- [Programowanie przy użyciu podstawowych zestawów międzyoperacyjnych](https://msdn.microsoft.com/library/306fa1d6-0703-4004-9e93-d0a57f1be81e(v=vs.100))
- [Lokalizowanie podstawowych zestawów międzyoperacyjnych](https://msdn.microsoft.com/library/d6768e4b-cd80-414d-a4f8-05d979eb393b(v=vs.100))
- [Redystrybucja podstawowych zestawów międzyoperacyjnych](https://msdn.microsoft.com/library/e76384f0-d631-474c-bdbd-13884cba0265(v=vs.100))