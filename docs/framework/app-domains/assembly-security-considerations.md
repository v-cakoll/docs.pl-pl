---
title: Zagadnienia dotyczące zabezpieczeń zestawów
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], security
- signcodes
- names [.NET Framework], assemblies
- strong-named assemblies, security considerations
- signing assemblies
- assemblies [.NET Framework], signing
- granting permissions, assemblies
- assemblies [.NET Framework], strong-named
- names [.NET Framework], strong names
- permissions [.NET Framework], assemblies
- security [.NET Framework], assemblies
- integrity with assemblies
ms.assetid: 1b5439c1-f3d5-4529-bd69-01814703d067
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e74d7a4a72b9595d6a280a16ad9bbc4118648404
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705704"
---
# <a name="assembly-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń zestawów
<a name="top"></a> Podczas kompilowania zestawu można określić zestaw uprawnień, które będą wymagane do uruchomienia. To, czy określone uprawnienia są przyznane do zestawu, czy nie, zależy od dowodów.  
  
 Istnieją dwa wyraźnie różniące się sposoby używania dowodów:  
  
- Dowód wejściowy jest scalany z dowodami zebranymi przez moduł ładujący w celu utworzenia ostatecznego zestawu dowodów stosowanego do rozpoznawania zasad. Metody używające tej semantyki obejmować **Assembly.Load**, **Assembly.LoadFrom**, i **Activator.CreateInstance**.  
  
- Dowód wejściowy jest używany w niezmienionej formie jako ostateczny zestaw dowodów stosowanych do rozpoznawania zasad. Metody używające tej semantyki obejmować **Assembly.Load(byte[])** i **AppDomain.DefineDynamicAssembly()**.  
  
 Opcjonalne uprawnienia mogą być przyznawane przez [zasady zabezpieczeń](../../../docs/framework/misc/code-access-security-basics.md) ustawił na komputerze, gdzie zestaw będzie działał. Jeśli kod ma obsługiwać wszystkie potencjalne wyjątki zabezpieczeń, można wykonać jedną z następujących czynności:  
  
- Wstawić żądania o uprawnienia dla wszystkich uprawnień, których wymaga kod, oraz obsługiwać z wyprzedzeniem niepowodzenia w czasie ładowania, które występują w razie nieprzyznania uprawnień.  
  
- W celu uzyskania uprawnień wymaganych przez kod nie używać żądań o uprawnienia, ale przygotować się na obsługę wyjątków zabezpieczeń w razie nieprzyznania uprawnień.  
  
    > [!NOTE]
    >  Zabezpieczenia to skomplikowana dziedzina, w której istnieje wiele opcji do wyboru. Aby uzyskać więcej informacji, zobacz [podstawowe pojęcia dotyczące zabezpieczeń](../../../docs/standard/security/key-security-concepts.md).  
  
 Podczas ładowania dowód zestawu jest wykorzystywany jako dane wejściowe dla zasad zabezpieczeń. Zasady zabezpieczeń są ustalane przez przedsiębiorstwo i administratora komputera, a także przez ustawienia zasad użytkownika. Określają one zestaw uprawnień przydzielanych całemu zarządzanemu kodowi podczas wykonywania. Zasady zabezpieczeń można ustanowić dla wydawcy zestawu (jeśli ma on podpis wygenerowany przez narzędzie do podpisywania), dla witryny internetowej i strefy (w znaczeniu używanym w programie Internet Explorer), z której zestaw został pobrany, lub dla silnej nazwy zestawu. Na przykład administrator komputera może ustanowić zasady zabezpieczeń, które pozwalają, aby kod pobrany z witryny internetowej i podpisany przez producenta danego oprogramowania miał dostęp do bazy danych na komputerze, ale nie przyznają dostępu umożliwiającego zapis na dysku komputera.  
  
## <a name="strong-named-assemblies-and-signing-tools"></a>Zestawy o silnej nazwie i narzędzia podpisywania  

 > [!WARNING]
 > Nie należy polegać na silne nazwy dla zabezpieczeń. Zapewniają one tylko unikatową tożsamość.

 Zestaw można podpisać na dwa różne, ale uzupełniające się sposoby: za pomocą silnej nazwy lub za pomocą [SignTool.exe (narzędzie podpisywania)](../../../docs/framework/tools/signtool-exe.md). Podpisywanie zestawu silną nazwą dodaje szyfrowanie kluczem publicznym do pliku zawierającego manifest zestawu. Podpisywanie za pomocą silnej nazwy pomaga zweryfikować unikatowość nazwy, zapobiec podszywaniu się pod nazwę oraz dostarczyć obiektom wywołującym jakąś tożsamość podczas rozpoznawania odwołań.  
  
 Żaden poziom zaufania jest skojarzony z silną nazwą, co sprawia, że [SignTool.exe (narzędzie podpisywania)](../../../docs/framework/tools/signtool-exe.md) ważne. Te dwa narzędzia podpisywania wymagają, aby wydawca potwierdził swoją tożsamość wobec zewnętrznego urzędu i uzyskał certyfikat. Certyfikat jest następnie osadzany w pliku i na jego podstawie administrator może decydować, czy ufa autentyczności kodu.  
  
 Można nadać silną nazwę i podpis cyfrowy utworzony przy użyciu [SignTool.exe (narzędzie podpisywania)](../../../docs/framework/tools/signtool-exe.md) do zestawu, lub możesz użyć dowolnej samodzielnie. Oba narzędzia podpisywania mogą podpisywać tylko jeden plik jednocześnie. W przypadku zestawu wieloplikowego podpisuje się plik zawierający manifest zestawu. Silna nazwa jest przechowywana w pliku zawierającego manifest zestawu, ale podpis utworzony za pomocą [SignTool.exe (narzędzie podpisywania)](../../../docs/framework/tools/signtool-exe.md) znajduje się w zarezerwowanym gnieździe w pliku wykonalnego (PE) pliku zawierającego manifest zestawu. Podpisywanie zestawu za pomocą [SignTool.exe (narzędzie podpisywania)](../../../docs/framework/tools/signtool-exe.md) mogą być używane (z lub bez silnej nazwy) Jeśli masz już hierarchia zaufania, która opiera się na[SignTool.exe (narzędzie podpisywania)](../../../docs/framework/tools/signtool-exe.md) generowane podpisów lub kiedy zasady używa tylko część klucza, a nie sprawdza łańcuch zaufania.  
  
> [!NOTE]
>  Jeśli do zestawu ma być stosowana silna nazwa i podpis z narzędzia podpisywania, najpierw należy przypisać silną nazwę.  
  
 Środowisko uruchomieniowe języka wspólnego również dokonuje weryfikacji skrótu. Manifest zestawu zawiera listę wszystkich plików tworzących zestaw, a także skrót każdego pliku utworzony podczas kompilowania manifestu. Przy wczytywaniu każdego pliku jego wartość jest skracana i porównywana z wartością skrótu przechowywaną w manifeście. Jeśli skróty różnią się od siebie, zestaw nie jest wczytywany.  
  
 Ponieważ stosowanie silnych nazw i podpisywanie przy użyciu narzędzia [SignTool.exe (narzędzie podpisywania)](../../../docs/framework/tools/signtool-exe.md) gwarantują integralność, zasady zabezpieczeń dostępu kodu można oprzeć na tych dwóch formach dowodu zestawu. Silne nazewnictwo i podpisywanie przy użyciu narzędzia [SignTool.exe (narzędzie podpisywania)](../../../docs/framework/tools/signtool-exe.md) gwarantuje integralność Dzięki podpisom cyfrowym i certyfikatom. Wszystkie wymienione technologie — wyznaczania wartości skrótu weryfikacji, silne nazwy i podpisywanie przy użyciu narzędzia [SignTool.exe (narzędzie podpisywania)](../../../docs/framework/tools/signtool-exe.md)— działają razem w celu zapewnienia zestawu nie została zmodyfikowana w dowolny sposób.  
  
## <a name="see-also"></a>Zobacz także

- [Zestawy o silnych nazwach](../../../docs/framework/app-domains/strong-named-assemblies.md)
- [Zestawy w środowisku uruchomieniowym CLR](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [SignTool.exe (narzędzie podpisywania)](../../../docs/framework/tools/signtool-exe.md)
