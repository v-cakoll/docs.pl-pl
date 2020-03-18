---
title: Zagadnienia dotyczące zabezpieczeń zestawów
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
ms.openlocfilehash: 77c9f9131b556e0b8fa639cd723bf1ca8cd6602e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73972306"
---
# <a name="assembly-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń zestawów
Podczas tworzenia zestawu można określić zestaw uprawnień, które zestaw wymaga do uruchomienia. To, czy określone uprawnienia są przyznane do zestawu, czy nie, zależy od dowodów.  
  
 Istnieją dwa wyraźnie różniące się sposoby używania dowodów:  
  
- Dowód wejściowy jest scalany z dowodami zebranymi przez moduł ładujący w celu utworzenia ostatecznego zestawu dowodów stosowanego do rozpoznawania zasad. Metody, które używają tej semantyczne obejmują **Assembly.Load**, **Assembly.LoadFrom**i **Activator.CreateInstance**.  
  
- Dowód wejściowy jest używany w niezmienionej formie jako ostateczny zestaw dowodów stosowanych do rozpoznawania zasad. Metody, które używają tej semantyczne obejmują **Assembly.Load(byte[])** i **AppDomain.DefineDynamicAssembly()**.  
  
  Opcjonalne uprawnienia mogą być przyznawane przez [zasady zabezpieczeń](../../framework/misc/code-access-security-basics.md) ustawione na komputerze, na którym będzie uruchamiany zestaw. Jeśli kod ma obsługiwać wszystkie potencjalne wyjątki zabezpieczeń, można wykonać jedną z następujących czynności:  
  
- Wstawić żądania o uprawnienia dla wszystkich uprawnień, których wymaga kod, oraz obsługiwać z wyprzedzeniem niepowodzenia w czasie ładowania, które występują w razie nieprzyznania uprawnień.  
  
- W celu uzyskania uprawnień wymaganych przez kod nie używać żądań o uprawnienia, ale przygotować się na obsługę wyjątków zabezpieczeń w razie nieprzyznania uprawnień.  
  
  > [!NOTE]
  > Zabezpieczenia to skomplikowana dziedzina, w której istnieje wiele opcji do wyboru. Aby uzyskać więcej informacji, zobacz [Kluczowe pojęcia zabezpieczeń](../../standard/security/key-security-concepts.md).  
  
 Podczas ładowania dowód zestawu jest wykorzystywany jako dane wejściowe dla zasad zabezpieczeń. Zasady zabezpieczeń są ustalane przez przedsiębiorstwo i administratora komputera, a także przez ustawienia zasad użytkownika. Określają one zestaw uprawnień przydzielanych całemu zarządzanemu kodowi podczas wykonywania. Zasady zabezpieczeń można ustanowić dla wydawcy zestawu (jeśli ma on podpis wygenerowany przez narzędzie do podpisywania), dla witryny internetowej i strefy (w znaczeniu używanym w programie Internet Explorer), z której zestaw został pobrany, lub dla silnej nazwy zestawu. Na przykład administrator komputera może ustanowić zasady zabezpieczeń, które pozwalają, aby kod pobrany z witryny internetowej i podpisany przez producenta danego oprogramowania miał dostęp do bazy danych na komputerze, ale nie przyznają dostępu umożliwiającego zapis na dysku komputera.  
  
## <a name="strong-named-assemblies-and-signing-tools"></a>Zestawy o silnych nazwach i narzędzia do podpisywania  

 > [!WARNING]
 > Nie należy polegać na silne nazwy dla bezpieczeństwa. Zapewniają one tylko unikatową tożsamość.

 Zestaw można podpisać na dwa różne, ale uzupełniające się sposoby: pod silną nazwą lub za pomocą [signtool.exe (Narzędzie podpisywania)](../../framework/tools/signtool-exe.md). Podpisywanie zestawu o silnej nazwie dodaje szyfrowanie klucza publicznego do pliku zawierającego manifest zestawu. Podpisywanie za pomocą silnej nazwy pomaga zweryfikować unikatowość nazwy, zapobiec podszywaniu się pod nazwę oraz dostarczyć obiektom wywołującym jakąś tożsamość podczas rozpoznawania odwołań.  
  
 Żaden poziom zaufania nie jest skojarzony z silną nazwą, co sprawia, że [signtool.exe (narzędzie podpisywania)](../../framework/tools/signtool-exe.md) jest ważne. Te dwa narzędzia podpisywania wymagają, aby wydawca potwierdził swoją tożsamość wobec zewnętrznego urzędu i uzyskał certyfikat. Certyfikat jest następnie osadzany w pliku i na jego podstawie administrator może decydować, czy ufa autentyczności kodu.  
  
 Można nadać zestawowi zarówno silną nazwę, jak i podpis cyfrowy utworzony przy użyciu [programu SignTool.exe (Narzędzie podpisywania)](../../framework/tools/signtool-exe.md) lub użyć samodzielnie. Oba narzędzia podpisywania mogą podpisywać tylko jeden plik jednocześnie. W przypadku zestawu wieloplikowego podpisuje się plik zawierający manifest zestawu. Silna nazwa jest przechowywana w pliku zawierającym manifest zestawu, ale podpis utworzony przy użyciu [signtool.exe (Narzędzie podpisywania)](../../framework/tools/signtool-exe.md) jest przechowywany w zarezerwowanym gnieciu w przenośnym pliku wykonywalnym (PE) zawierającym manifest zestawu. Podpisywanie zestawu za pomocą [SignTool.exe (Narzędzie podpisywania)](../../framework/tools/signtool-exe.md) może być używane (z lub bez silnej nazwy), gdy masz już hierarchię zaufania, która opiera się na [signtool.exe (Narzędzie podpisywania)](../../framework/tools/signtool-exe.md) wygenerowane podpisy lub gdy zasady używa tylko części klucza i nie sprawdza łańcucha zaufania.  
  
> [!NOTE]
> Jeśli do zestawu ma być stosowana silna nazwa i podpis z narzędzia podpisywania, najpierw należy przypisać silną nazwę.  
  
 Środowisko uruchomieniowe języka wspólnego również dokonuje weryfikacji skrótu. Manifest zestawu zawiera listę wszystkich plików tworzących zestaw, a także skrót każdego pliku utworzony podczas kompilowania manifestu. Przy wczytywaniu każdego pliku jego wartość jest skracana i porównywana z wartością skrótu przechowywaną w manifeście. Jeśli skróty różnią się od siebie, zestaw nie jest wczytywany.  
  
 Ponieważ silne nazewnictwa i podpisywania przy użyciu [SignTool.exe (Narzędzie podpisywania)](../../framework/tools/signtool-exe.md) gwarantuje integralność, można oprzeć zasady zabezpieczeń dostępu do kodu na tych dwóch form dowodów zestawu. Silne nazewnictwo i podpisywanie za pomocą [signtool.exe (Narzędzie podpisywania)](../../framework/tools/signtool-exe.md) gwarantuje integralność za pomocą podpisów cyfrowych i certyfikatów. Wszystkie wymienione technologie — weryfikacja skrótów, silne nazewnictwo i podpisywanie za pomocą [signtool.exe (Narzędzie podpisywania)](../../framework/tools/signtool-exe.md)— współpracują ze sobą, aby upewnić się, że zestaw nie został w żaden sposób zmieniony.  
  
## <a name="see-also"></a>Zobacz też

- [Zestawy o silnych nazwach](strong-named.md)
- [Zestawy w środowisku .NET](index.md)
- [SignTool.exe (narzędzie podpisywania)](../../framework/tools/signtool-exe.md)
