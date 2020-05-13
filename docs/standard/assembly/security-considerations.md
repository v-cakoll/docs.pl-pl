---
title: Zagadnienia dotyczące zabezpieczeń zestawów
description: Podczas kompilowania zestawu .NET można określić uprawnienia wymagane przez zestaw do uruchomienia. W tym artykule omówiono zestawy o silnych nazwach i narzędzia podpisywania.
ms.date: 08/20/2019
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
ms.openlocfilehash: 7f897241b121cf1bd52d02ee5f487aeafafc3cb0
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378660"
---
# <a name="assembly-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń zestawów
Podczas kompilowania zestawu można określić zestaw uprawnień wymaganych do uruchomienia zestawu. To, czy określone uprawnienia są przyznane do zestawu, czy nie, zależy od dowodów.  
  
 Istnieją dwa wyraźnie różniące się sposoby używania dowodów:  
  
- Dowód wejściowy jest scalany z dowodami zebranymi przez moduł ładujący w celu utworzenia ostatecznego zestawu dowodów stosowanego do rozpoznawania zasad. Metody używające tej semantyki obejmują **Assembly. Load**, **Assembly. LoadFrom**i **aktywator. CreateInstance**.  
  
- Dowód wejściowy jest używany w niezmienionej formie jako ostateczny zestaw dowodów stosowanych do rozpoznawania zasad. Metody używające tej semantyki obejmują **zestaw. Load (Byte [])** i **AppDomain. DefineDynamicAssembly ()**.  
  
  Uprawnienia opcjonalne mogą być przyznawane [zasadom zabezpieczeń](../../framework/misc/code-access-security-basics.md) ustawionym na komputerze, na którym zostanie uruchomiony zestaw. Jeśli kod ma obsługiwać wszystkie potencjalne wyjątki zabezpieczeń, można wykonać jedną z następujących czynności:  
  
- Wstawić żądania o uprawnienia dla wszystkich uprawnień, których wymaga kod, oraz obsługiwać z wyprzedzeniem niepowodzenia w czasie ładowania, które występują w razie nieprzyznania uprawnień.  
  
- W celu uzyskania uprawnień wymaganych przez kod nie używać żądań o uprawnienia, ale przygotować się na obsługę wyjątków zabezpieczeń w razie nieprzyznania uprawnień.  
  
  > [!NOTE]
  > Zabezpieczenia to skomplikowana dziedzina, w której istnieje wiele opcji do wyboru. Aby uzyskać więcej informacji, zobacz podstawowe [pojęcia dotyczące zabezpieczeń](../../standard/security/key-security-concepts.md).  
  
 Podczas ładowania dowód zestawu jest wykorzystywany jako dane wejściowe dla zasad zabezpieczeń. Zasady zabezpieczeń są ustalane przez przedsiębiorstwo i administratora komputera, a także przez ustawienia zasad użytkownika. Określają one zestaw uprawnień przydzielanych całemu zarządzanemu kodowi podczas wykonywania. Zasady zabezpieczeń można ustanowić dla wydawcy zestawu (jeśli ma on podpis wygenerowany przez narzędzie do podpisywania), dla witryny internetowej i strefy (w znaczeniu używanym w programie Internet Explorer), z której zestaw został pobrany, lub dla silnej nazwy zestawu. Na przykład administrator komputera może ustanowić zasady zabezpieczeń, które pozwalają, aby kod pobrany z witryny internetowej i podpisany przez producenta danego oprogramowania miał dostęp do bazy danych na komputerze, ale nie przyznają dostępu umożliwiającego zapis na dysku komputera.  
  
## <a name="strong-named-assemblies-and-signing-tools"></a>Zestawy o silnych nazwach i narzędzia podpisywania  

 > [!WARNING]
 > Nie należy polegać na silnych nazwach zabezpieczeń. Zapewniają one tylko unikatową tożsamość.

 Zestaw można podpisać na dwa różne, ale uzupełniające sposoby: za pomocą silnej nazwy lub przy użyciu [Narzędzia SignTool. exe (Narzędzie podpisywania)](../../framework/tools/signtool-exe.md). Podpisywanie zestawu o silnej nazwie dodaje szyfrowanie klucza publicznego do pliku zawierającego manifest zestawu. Podpisywanie za pomocą silnej nazwy pomaga zweryfikować unikatowość nazwy, zapobiec podszywaniu się pod nazwę oraz dostarczyć obiektom wywołującym jakąś tożsamość podczas rozpoznawania odwołań.  
  
 Żaden poziom zaufania nie jest skojarzony z silną nazwą, co oznacza, że [Narzędzia SignTool. exe (Narzędzie podpisywania)](../../framework/tools/signtool-exe.md) ważne. Te dwa narzędzia podpisywania wymagają, aby wydawca potwierdził swoją tożsamość wobec zewnętrznego urzędu i uzyskał certyfikat. Certyfikat jest następnie osadzany w pliku i na jego podstawie administrator może decydować, czy ufa autentyczności kodu.  
  
 Możesz nadać zarówno silną nazwę, jak i podpis cyfrowy utworzony przy użyciu [Narzędzia SignTool. exe (Narzędzie podpisywania)](../../framework/tools/signtool-exe.md) do zestawu lub użyć dowolnego z nich. Oba narzędzia podpisywania mogą podpisywać tylko jeden plik jednocześnie. W przypadku zestawu wieloplikowego podpisuje się plik zawierający manifest zestawu. Silna nazwa jest przechowywana w pliku zawierającym manifest zestawu, ale sygnatura utworzona za pomocą [Narzędzia SignTool. exe (Narzędzie podpisywania)](../../framework/tools/signtool-exe.md) jest przechowywana w zastrzeżonym miejscu w przenośnym pliku wykonywalnym (PE) zawierającym manifest zestawu. Podpisywanie zestawu za pomocą [Narzędzia SignTool. exe (Narzędzie podpisywania)](../../framework/tools/signtool-exe.md) może być używane (z silną nazwą lub bez niej), gdy istnieje już Hierarchia zaufania, która opiera się na wygenerowanych sygnaturach [Narzędzia SignTool. exe (Narzędzie podpisywania)](../../framework/tools/signtool-exe.md) lub gdy zasady używają tylko części klucza i nie sprawdzają łańcucha zaufania.  
  
> [!NOTE]
> Jeśli do zestawu ma być stosowana silna nazwa i podpis z narzędzia podpisywania, najpierw należy przypisać silną nazwę.  
  
 Środowisko uruchomieniowe języka wspólnego również dokonuje weryfikacji skrótu. Manifest zestawu zawiera listę wszystkich plików tworzących zestaw, a także skrót każdego pliku utworzony podczas kompilowania manifestu. Przy wczytywaniu każdego pliku jego wartość jest skracana i porównywana z wartością skrótu przechowywaną w manifeście. Jeśli skróty różnią się od siebie, zestaw nie jest wczytywany.  
  
 Ze względu na to, że silne nazewnictwo i podpisywanie przy użyciu [Narzędzia Narzędzia SignTool. exe (Narzędzie podpisywania)](../../framework/tools/signtool-exe.md) gwarantuje integralność, zasady zabezpieczeń dostępu kodu są oparte na tych dwóch formach dowodu zestawu. Silne nazewnictwo i podpisywanie przy użyciu [Narzędzia SignTool. exe (Narzędzie podpisywania)](../../framework/tools/signtool-exe.md) gwarantuje integralność za pośrednictwem podpisów cyfrowych i certyfikatów. Wszystkie wymienione technologie — weryfikacja skrótu, silne nazewnictwo i podpisywanie przy użyciu [Narzędzia SignTool. exe (Narzędzie podpisywania)](../../framework/tools/signtool-exe.md)— działają razem, aby upewnić się, że zestaw nie został zmieniony w żaden sposób.  
  
## <a name="see-also"></a>Zobacz też

- [Zestawy o silnych nazwach](strong-named.md)
- [Zestawy w środowisku .NET](index.md)
- [Narzędzia SignTool. exe (Narzędzie podpisywania)](../../framework/tools/signtool-exe.md)
