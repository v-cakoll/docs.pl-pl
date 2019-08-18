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
ms.openlocfilehash: fc4ff8f914f0e049a0fdf27b5008b1e39bc40116
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566782"
---
# <a name="delay-signing-an-assembly"></a>Opóźnione podpisywanie zestawu
Organizacja może mieć dokładnie chronioną parę kluczy, do której deweloperzy nie mają dostępu codziennie. Klucz publiczny jest często dostępny, ale dostęp do klucza prywatnego jest ograniczony tylko do kilku osób. Podczas tworzenia zestawów o silnych nazwach każdy zestaw, który odwołuje się do zestawu o silnej nazwie, zawiera token klucza publicznego, który jest używany do nadawania silnej nazwy zestawu docelowego. Wymaga to, aby klucz publiczny był dostępny podczas procesu tworzenia.  
  
 Możesz użyć opóźnionego lub częściowego podpisywania w czasie kompilacji, aby zarezerwować miejsce w przenośnym pliku wykonywalnym (PE) dla sygnatury silnej nazwy, ale odroczyć rzeczywiste podpisywanie do pewnego późniejszego etapu (zazwyczaj przed wysyłką zestawu).  
  
 Poniższe kroki przedstawiają proces opóźnienia podpisywania zestawu:  
  
1. Uzyskaj część klucza publicznego pary kluczy od organizacji, która będzie podpisywać ostateczne. Zazwyczaj ten klucz jest w formie pliku. snk, który można utworzyć za pomocą [Narzędzia silnej nazwy (SN. exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) dostarczonego przez Windows SDK.  
  
2. Dodaj adnotację do kodu źródłowego dla zestawu z dwoma atrybutami niestandardowymi z <xref:System.Reflection>:  
  
    - <xref:System.Reflection.AssemblyKeyFileAttribute>, który przekazuje nazwę pliku zawierającego klucz publiczny jako parametr do jego konstruktora.  
  
    - <xref:System.Reflection.AssemblyDelaySignAttribute>, co oznacza, że jest używane podpisywanie opóźnień, przekazując **wartość true** jako parametr do jego konstruktora. Na przykład:  
  
         [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
         [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
         [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
3. Kompilator wstawia klucz publiczny do manifestu zestawu i rezerwuje miejsce w pliku PE w celu uzyskania pełnej sygnatury silnej nazwy. Prawdziwy klucz publiczny musi być przechowywany podczas tworzenia zestawu, tak aby inne zestawy odwołujące się do tego zestawu mogły uzyskać klucz do przechowywania we własnym odwołaniu do zestawu.  
  
4. Ponieważ zestaw nie ma prawidłowego podpisu silnej nazwy, weryfikacja tej sygnatury musi być wyłączona. Można to zrobić za pomocą opcji **– VR** za pomocą narzędzia silnej nazwy.  
  
     Poniższy przykład wyłącza weryfikację dla zestawu o nazwie `myAssembly.dll`.  
  
    ```  
    sn –Vr myAssembly.dll  
    ```  
  
     Aby wyłączyć weryfikację na platformach, w których nie można uruchomić narzędzia silnej nazwy, na przykład mikroprocesorów Advanced RISC Machine (ARM), użyj opcji **– VK** , aby utworzyć plik rejestru. Zaimportuj plik rejestru do rejestru na komputerze, na którym chcesz wyłączyć weryfikację. Poniższy przykład tworzy plik rejestru dla `myAssembly.dll`.  
  
    ```  
    sn –Vk myRegFile.reg myAssembly.dll  
    ```  
  
     Za pomocą opcji **– VR** lub **– VK** można opcjonalnie dołączyć plik. snk do podpisywania klucza testowego.  
  
    > [!WARNING]
    > Nie należy polegać na silnych nazwach zabezpieczeń. Zapewniają one tylko unikatową tożsamość.
  
    > [!NOTE]
    >  Jeśli używasz opóźnienia podpisywania podczas opracowywania w programie Visual Studio na komputerze 64-bitowym i kompilujesz zestaw dla **dowolnego procesora**, może być konieczne dwukrotne zastosowanie opcji **-VR** . (W programie Visual Studio **każdy procesor CPU** jest wartością właściwości kompilacji **docelowej platformy** ; podczas kompilowania z wiersza polecenia jest to wartość domyślna). Aby uruchomić aplikację z poziomu wiersza polecenia lub Eksploratora plików, użyj 64-bitowej wersji [SN. exe (Narzędzie silnej nazwy)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) , aby zastosować opcję **-VR** do zestawu. Aby załadować zestaw do programu Visual Studio w czasie projektowania (na przykład jeśli zestaw zawiera składniki, które są używane przez inne zestawy w aplikacji), użyj 32-bitowej wersji narzędzia silnej nazwy. Dzieje się tak, ponieważ kompilator just-in-Time (JIT) kompiluje zestaw do 64-bitowego kodu natywnego, gdy zestaw jest uruchamiany z wiersza polecenia i do 32-bitowy kod natywny, gdy zestaw jest ładowany do środowiska czasu projektowania.  
  
5. Później, zazwyczaj tuż przed wysyłką, przesyłasz zestaw do urzędu podpisywania w organizacji w celu zapewnienia rzeczywistego podpisywania silnej nazwy przy użyciu opcji **– R** z narzędziem silnej nazwy.  
  
     Poniższy przykład podpisuje zestaw `myAssembly.dll` o silnej nazwie `sgKey.snk` przy użyciu pary kluczy.  
  
    ```  
    sn -R myAssembly.dll sgKey.snk  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie zestawów](../../../docs/framework/app-domains/create-assemblies.md)
- [Instrukcje: Tworzenie pary kluczy publiczny-prywatny](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [Sn.exe (narzędzie silnych nazw)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)
