---
title: "Zagadnienia dotyczące zabezpieczeń zestawów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 11c66af3a855dac649d5f09944d68fb77a0e8619
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń zestawów
<a name="top"></a>Podczas kompilowania zestawu można określić zestaw uprawnień wymaganych do uruchomienia zestawu. To, czy określone uprawnienia są przyznane do zestawu, czy nie, zależy od dowodów.  
  
 Istnieją dwa wyraźnie różniące się sposoby używania dowodów:  
  
-   Dowód wejściowy jest scalany z dowodami zebranymi przez moduł ładujący w celu utworzenia ostatecznego zestawu dowodów stosowanego do rozpoznawania zasad. Metody, korzystających z tym semantycznego obejmują **metody Assembly.Load**, **Assembly.LoadFrom**, i **metody Activator.CreateInstance**.  
  
-   Dowód wejściowy jest używany w niezmienionej formie jako ostateczny zestaw dowodów stosowanych do rozpoznawania zasad. Metody, korzystających z tym semantycznego obejmują **Assembly.Load(byte[])** i **AppDomain.DefineDynamicAssembly()**.  
  
 Opcjonalnie można uprawnienia przez [zasady zabezpieczeń](../../../docs/framework/misc/code-access-security-basics.md) wartości na komputerze, w którym będzie uruchamiane zestawu. Jeśli kod ma obsługiwać wszystkie potencjalne wyjątki zabezpieczeń, można wykonać jedną z następujących czynności:  
  
-   Wstawić żądania o uprawnienia dla wszystkich uprawnień, których wymaga kod, oraz obsługiwać z wyprzedzeniem niepowodzenia w czasie ładowania, które występują w razie nieprzyznania uprawnień.  
  
-   W celu uzyskania uprawnień wymaganych przez kod nie używać żądań o uprawnienia, ale przygotować się na obsługę wyjątków zabezpieczeń w razie nieprzyznania uprawnień.  
  
    > [!NOTE]
    >  Zabezpieczenia to skomplikowana dziedzina, w której istnieje wiele opcji do wyboru. Aby uzyskać więcej informacji, zobacz [podstawowe pojęcia dotyczące zabezpieczeń](../../../docs/standard/security/key-security-concepts.md).  
  
 Podczas ładowania dowód zestawu jest wykorzystywany jako dane wejściowe dla zasad zabezpieczeń. Zasady zabezpieczeń są ustalane przez przedsiębiorstwo i administratora komputera, a także przez ustawienia zasad użytkownika. Określają one zestaw uprawnień przydzielanych całemu zarządzanemu kodowi podczas wykonywania. Zasady zabezpieczeń można ustanowić dla wydawcy zestawu (jeśli ma on podpis wygenerowany przez narzędzie do podpisywania), dla witryny internetowej i strefy (w znaczeniu używanym w programie Internet Explorer), z której zestaw został pobrany, lub dla silnej nazwy zestawu. Na przykład administrator komputera może ustanowić zasady zabezpieczeń, które pozwalają, aby kod pobrany z witryny internetowej i podpisany przez producenta danego oprogramowania miał dostęp do bazy danych na komputerze, ale nie przyznają dostępu umożliwiającego zapis na dysku komputera.  
  
## <a name="strong-named-assemblies-and-signing-tools"></a>Zestawy o silnej nazwie i narzędzia podpisywania  
 Można podpisać zestawu na dwa sposoby różne, ale uzupełniające: przy użyciu silnej nazwy lub za pomocą [SignTool.exe (narzędzie podpisu)](../../../docs/framework/tools/signtool-exe.md). Podpisywanie zestawu silną nazwą dodaje szyfrowanie klucza publicznego do pliku zawierającego manifest zestawu. Podpisywanie za pomocą silnej nazwy pomaga zweryfikować unikatowość nazwy, zapobiec podszywaniu się pod nazwę oraz dostarczyć obiektom wywołującym jakąś tożsamość podczas rozpoznawania odwołań.  
  
 Jednak żaden poziom zaufania jest skojarzony z nazwą silną, dzięki czemu [SignTool.exe (narzędzie podpisu)](../../../docs/framework/tools/signtool-exe.md) ważne. Te dwa narzędzia podpisywania wymagają, aby wydawca potwierdził swoją tożsamość wobec zewnętrznego urzędu i uzyskał certyfikat. Certyfikat jest następnie osadzany w pliku i na jego podstawie administrator może decydować, czy ufa autentyczności kodu.  
  
 Można podać zarówno silnej nazwy i podpisu cyfrowego utworzone za pomocą [SignTool.exe (narzędzie podpisu)](../../../docs/framework/tools/signtool-exe.md) do zestawu, lub można użyć tylko. Oba narzędzia podpisywania mogą podpisywać tylko jeden plik jednocześnie. W przypadku zestawu wieloplikowego podpisuje się plik zawierający manifest zestawu. Silnej nazwy jest przechowywana w pliku manifestu zestawu zawierającego, ale podpisu utworzone za pomocą [SignTool.exe (narzędzie podpisu)](../../../docs/framework/tools/signtool-exe.md) są przechowywane w gnieździe zastrzeżone przenośny plik wykonywalny (PE) zawierający manifest zestawu. Podpisywanie zestawu za pomocą [SignTool.exe (narzędzie podpisu)](../../../docs/framework/tools/signtool-exe.md) można używać (z lub bez silnej nazwy) Jeśli już masz hierarchia zaufania, który korzysta[SignTool.exe (narzędzie podpisu)](../../../docs/framework/tools/signtool-exe.md) wygenerowany podpisów lub gdy zasady używa tylko część klucza i nie sprawdza łańcuch zaufania.  
  
> [!NOTE]
>  Jeśli do zestawu ma być stosowana silna nazwa i podpis z narzędzia podpisywania, najpierw należy przypisać silną nazwę.  
  
 Środowisko uruchomieniowe języka wspólnego również dokonuje weryfikacji skrótu. Manifest zestawu zawiera listę wszystkich plików tworzących zestaw, a także skrót każdego pliku utworzony podczas kompilowania manifestu. Przy wczytywaniu każdego pliku jego wartość jest skracana i porównywana z wartością skrótu przechowywaną w manifeście. Jeśli skróty różnią się od siebie, zestaw nie jest wczytywany.  
  
 Ponieważ silne nazewnictwo i podpisywanie przy użyciu [SignTool.exe (narzędzie podpisu)](../../../docs/framework/tools/signtool-exe.md) zagwarantowania spójności, można utworzyć zasad zabezpieczenia dostępu kodu na tych dwóch metod świadectwa zestawu. Silne nazewnictwo i podpisywanie przy użyciu [SignTool.exe (narzędzie podpisu)](../../../docs/framework/tools/signtool-exe.md) zagwarantować integralności za pomocą podpisów cyfrowych i certyfikatów. Te technologie wymienionych — skrótów weryfikacji, silne nazwy i podpisywanie przy użyciu [SignTool.exe (narzędzie podpisu)](../../../docs/framework/tools/signtool-exe.md)— działają razem, upewnij się, że zestaw nie zostały zmienione w dowolny sposób.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestawy o silnych nazwach](../../../docs/framework/app-domains/strong-named-assemblies.md)  
 [Zestawy w środowisko uruchomieniowe języka wspólnego](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [SignTool.exe (narzędzie podpisu)](../../../docs/framework/tools/signtool-exe.md)
