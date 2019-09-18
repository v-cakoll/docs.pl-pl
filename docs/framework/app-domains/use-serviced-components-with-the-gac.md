---
title: Używanie obsługiwanych składników z globalną pamięcią podręczną zestawów
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4edc675e0348f06114b8162022f1d9420e0cec52
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053062"
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a>Używanie obsługiwanych składników z globalną pamięcią podręczną zestawów
Składniki obsługiwane (zarządzane kod modelu COM+) należy umieścić w globalnej pamięci podręcznej zestawów. W niektórych scenariuszach środowisko uruchomieniowe języka wspólnego i usługi modelu COM+ mogą obsługiwać składniki obsługiwane przez program, które nie znajdują się w globalnej pamięci podręcznej zestawów; w innych scenariuszach nie mogą. Poniższe scenariusze ilustrują:  
  
- W przypadku składników usługi w aplikacji serwera COM+ zestaw zawierający składniki musi znajdować się w globalnej pamięci podręcznej zestawów, ponieważ program dllhost. exe nie działa w tym samym katalogu, w którym znajdują się składniki obsługiwane przez usługę.  
  
- W przypadku składników usługi w aplikacji biblioteki modelu COM+ środowisko uruchomieniowe i usługi COM+ mogą rozpoznać odwołanie do zestawu zawierającego składniki, wyszukując w bieżącym katalogu. W takim przypadku zestaw nie musi znajdować się w globalnej pamięci podręcznej zestawów.  
  
- W przypadku składników usługi w aplikacji ASP.NET sytuacja jest inna. Jeśli umieścisz zestaw zawierający składniki usługi w katalogu bin bazy aplikacji i użyjesz rejestracji na żądanie, zestaw będzie kopiowany w tle do pamięci podręcznej pobierania, ponieważ ASP.NET wykorzystuje możliwości w tle środowiska uruchomieniowego.  
  
## <a name="see-also"></a>Zobacz także

- [Praca z zestawami i globalną pamięcią podręczną zestawów](working-with-assemblies-and-the-gac.md)
- [Gacutil.exe (narzędzie Global Assembly Cache)](../tools/gacutil-exe-gac-tool.md)
