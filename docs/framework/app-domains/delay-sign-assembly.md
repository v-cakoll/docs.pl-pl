---
title: Opóźnione podpisywanie zestawu
ms.date: 07/31/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- deferring assembly signing
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, delaying assembly signing
- partial assembly signing
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4457bd6d5efd7404cdba6c5fbdbffa9f9eb62141
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="delay-signing-an-assembly"></a>Opóźnione podpisywanie zestawu
Organizacja może mieć ściśle związany parę kluczy, że deweloperzy nie mają dostępu do codziennie. Klucz publiczny często są dostępne, ale dostęp do klucza prywatnego jest ograniczony do tylko kilka osób. Podczas tworzenia zestawy o silnych nazwach, każdego zestawu tego zestawu docelowego odwołania o silnych nazwach zawiera token klucza publicznego używać, aby zapewnić silnej nazwy zestawu docelowego. To wymaga klucza publicznego dostępne podczas procesu projektowania.  
  
 Umożliwia opóźnione lub częściowe podpisywanie w czasie kompilacji zarezerwowanego miejsca w przenośny plik wykonywalny (PE) dla podpisu silnej nazwy, ale mają być odroczone rzeczywiste podpisywania do czasu późniejszym etapie (zwykle tylko przed dostarczeniem zestawu).  
  
 Poniższe kroki wchodzą w skład procesu opóźnione podpisywanie zestawu:  
  
1.  Uzyskaj publicznej części klucza o pary kluczy z organizacji, który będzie do ostatecznego podpisywania. Zazwyczaj ten klucz jest w formie pliku .snk —, które mogą być tworzone przy użyciu [narzędzie Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) dostarczonych przez [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
2.  Dodawanie adnotacji kodu źródłowego dla zestawu z dwóch atrybutów niestandardowych z <xref:System.Reflection>:  
  
    -   <xref:System.Reflection.AssemblyKeyFileAttribute>, która przekazuje nazwę pliku zawierającego klucz publiczny jako parametru dla jego konstruktora.  
  
    -   <xref:System.Reflection.AssemblyDelaySignAttribute>, co oznacza, że podpisywanie opóźnione jest używany przez przekazanie **true** jako parametru dla jego konstruktora. Na przykład:  
  
         [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
         [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
         [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
3.  Kompilator wstawia klucz publiczny w manifeście zestawu i rezerwuje miejsce w pliku PE pełnej silnego podpisu. Klucz publiczny rzeczywistym musi być przechowywany podczas zestaw skonstruowano, dzięki czemu inne zestawy, które odwołują się do tego zestawu można uzyskać klucz do przechowywania w odwołaniu do zestawu.  
  
4.  Ponieważ zestaw nie ma podpisu prawidłową silną nazwę, weryfikacja ten podpis musi być wyłączony. Można to zrobić za pomocą **— Vr** opcji za pomocą narzędzia silnej nazwy.  
  
     Poniższy przykład powoduje wyłączenie weryfikacji dla zestawu o nazwie `myAssembly.dll`.  
  
    ```  
    sn –Vr myAssembly.dll  
    ```  
  
     Aby wyłączyć funkcję weryfikacji na platformach, której nie można uruchomić narzędzie Strong Name, takich jak mikroprocesorami Advanced RISC Machine (ARM), należy użyć **— Vk** opcję, aby utworzyć plik rejestru. Importuj plik rejestru do rejestru na komputerze, w którym chcesz wyłączyć weryfikację. Poniższy przykład tworzy plik rejestru dla `myAssembly.dll`.  
  
    ```  
    sn –Vk myRegFile.reg myAssembly.dll  
    ```  
  
     Przy użyciu jednej **— Vr** lub **— Vk** opcji, można opcjonalnie dołączyć plik .snk — test klucza podpisywania.  
  
    > [!WARNING]
    > Nie należy polegać na silnych nazw zabezpieczeń. Udostępniają one tylko unikatową tożsamość.
  
    > [!NOTE]
    >  Jeśli używasz opóźnione podpisywanie podczas tworzenia z programem Visual Studio na komputerze 64-bitowych, i kompilowania zestawu pod kątem **Any CPU**, może być konieczne zastosowanie **- Vr** opcji dwa razy. (W programie Visual Studio, **Any CPU** jest wartością **platformy docelowej** kompilacji właściwości; podczas kompilowania z wiersza polecenia jest wartość domyślna.) Do uruchamiania aplikacji z poziomu wiersza polecenia lub w Eksploratorze plików, użyj wersji 64-bitowych [Sn.exe (narzędzie silnej nazwy)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) dotyczyć **- Vr** opcji do zestawu. Aby załadować zestawu do programu Visual Studio w czasie projektowania (np. zestaw zawiera składniki, które są używane przez innych zestawów w aplikacji), należy użyć 32-bitowej wersji narzędzia silnej nazwy. Jest to spowodowane przy użyciu kompilatora just in time (JIT) kompiluje zestawu natywnego kodu 64-bitowego zestawu jest uruchamiany z wiersza polecenia i 32-bitowego kodu natywnego, gdy zestaw jest ładowany do środowiska czasu projektowania.  
  
5.  Później, zwykle po prostu przed wysyłką, przesyłania podpisywania urzędu do rzeczywistego silnej nazwy podpisywanie przy użyciu zestawu do organizacji **– R** opcji za pomocą narzędzia silnej nazwy.  
  
     Poniższy przykład podpisuje zestawu o nazwie `myAssembly.dll` z przy użyciu silnej nazwy `sgKey.snk` parę kluczy.  
  
    ```  
    sn -R myAssembly.dll sgKey.snk  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie zestawów](../../../docs/framework/app-domains/create-assemblies.md)  
 [Instrukcje: tworzenie pary kluczy publiczny-prywatny](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [Sn.exe (narzędzie silnych nazw)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)
