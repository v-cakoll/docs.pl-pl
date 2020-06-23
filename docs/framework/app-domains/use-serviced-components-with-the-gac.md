---
title: Używanie obsługiwanych składników z globalną pamięcią podręczną zestawów
description: Korzystaj z serwisowanych składników (składników kodu modelu COM+) z globalną pamięcią podręczną zestawów w programie .NET. Sprawdź, czy usługi CLR i COM+ mogą obsługiwać składniki nie korzystające z pamięci podręcznej.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
ms.openlocfilehash: 6b7371865b7b1cedda0ee03b2cc28c74b5c3da0b
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104477"
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a>Używanie obsługiwanych składników z globalną pamięcią podręczną zestawów
Składniki obsługiwane (zarządzane kod modelu COM+) należy umieścić w globalnej pamięci podręcznej zestawów. W niektórych scenariuszach środowisko uruchomieniowe języka wspólnego i usługi modelu COM+ mogą obsługiwać składniki obsługiwane przez program, które nie znajdują się w globalnej pamięci podręcznej zestawów; w innych scenariuszach nie mogą. Poniższe scenariusze ilustrują:  
  
- W przypadku składników usługi w aplikacji serwera COM+ zestaw zawierający składniki musi znajdować się w globalnej pamięci podręcznej zestawów, ponieważ Dllhost.exe nie działa w tym samym katalogu, w którym znajdują się składniki obsługiwane przez usługę.  
  
- W przypadku składników usługi w aplikacji biblioteki modelu COM+ środowisko uruchomieniowe i usługi COM+ mogą rozpoznać odwołanie do zestawu zawierającego składniki, wyszukując w bieżącym katalogu. W takim przypadku zestaw nie musi znajdować się w globalnej pamięci podręcznej zestawów.  
  
- W przypadku składników usługi w aplikacji ASP.NET sytuacja jest inna. Jeśli umieścisz zestaw zawierający składniki usługi w katalogu bin bazy aplikacji i użyjesz rejestracji na żądanie, zestaw będzie kopiowany w tle do pamięci podręcznej pobierania, ponieważ ASP.NET wykorzystuje możliwości w tle środowiska uruchomieniowego.  
  
## <a name="see-also"></a>Zobacz też

- [Praca z zestawami i globalną pamięcią podręczną zestawów](working-with-assemblies-and-the-gac.md)
- [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md)
