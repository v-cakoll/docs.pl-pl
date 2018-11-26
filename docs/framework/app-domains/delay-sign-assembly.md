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
ms.openlocfilehash: 87346b28ff98c453949fe31aea4d0ef1880b0095
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2018
ms.locfileid: "52296341"
---
# <a name="delay-signing-an-assembly"></a>Opóźnione podpisywanie zestawu
Organizacja może mieć ściśle chronionej parę kluczy, że deweloperzy nie mają dostępu do codziennie. Klucz publiczny jest często dostępne, ale dostęp do klucza prywatnego jest ograniczony do tylko kilka osób. Podczas tworzenia zestawów o silnych nazwach, każdy zestaw ten zestaw docelowy o silnej nazwie odwołania zawiera token klucza publicznego, używać, aby zapewnić silnej nazwy zestawu docelowego. Wymaga to, czy klucz publiczny będą dostępne podczas procesu projektowania.  
  
 Opóźnione lub częściowe podpisywanie w czasie kompilacji służy do rezerwowania miejsca w przenośny plik wykonywalny (PE) dla podpisu silnej nazwy, ale Odrocz rzeczywiste podpisywania do czasu na późniejszym etapie (zazwyczaj po prostu przed dostarczeniem zestawu).  
  
 Poniższe kroki przedstawiają procedurę opóźnione podpisywanie zestawu:  
  
1.  Uzyskaj część z kluczem publicznym pary kluczy od organizacji, która będzie zajmować się ostateczną podpisywania. Zazwyczaj ten klucz jest w formie pliku .snk, które mogą być tworzone za pomocą [narzędzie silnych nazw (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) dostarczone przez [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
2.  Dodawanie adnotacji do kodu źródłowego dla zestawu za pomocą dwóch atrybutów niestandardowych z <xref:System.Reflection>:  
  
    -   <xref:System.Reflection.AssemblyKeyFileAttribute>, która przekazuje nazwę pliku zawierającego klucz publiczny jako parametr do jej konstruktora.  
  
    -   <xref:System.Reflection.AssemblyDelaySignAttribute>, co oznacza, że opóźnienie podpisywania jest używany przez przekazanie **true** jako parametr do jej konstruktora. Na przykład:  
  
         [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
         [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
         [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
3.  Kompilator wstawia klucz publiczny do manifestu zestawu i rezerwuje miejsce w pliku PE podpisu pełnej silnej nazwy. Rzeczywiste publicznego klucza musi być przechowywany, natomiast zestaw zaprojektowano tak, aby inne zestawy odwołujące się do tego zestawu można uzyskać klucz do przechowywania w odwołania do zestawu.  
  
4.  Ponieważ zestaw nie ma podpisu prawidłową silną nazwę, należy wyłączyć weryfikację ten podpis. Można to zrobić za pomocą **— Vr** opcji narzędzie silnych nazw.  
  
     Poniższy przykład powoduje wyłączenie weryfikacji dla zestawu o nazwie `myAssembly.dll`.  
  
    ```  
    sn –Vr myAssembly.dll  
    ```  
  
     Aby wyłączyć weryfikację na platformach gdzie nie można uruchomić narzędzie silnych nazw, takich jak mikroprocesory Advanced RISC Machine (ARM), należy użyć **— Vk** opcję, aby utworzyć plik rejestru. Importuj plik rejestru do rejestru na komputerze, w którym chcesz wyłączyć weryfikację. Poniższy przykład tworzy plik rejestru dla `myAssembly.dll`.  
  
    ```  
    sn –Vk myRegFile.reg myAssembly.dll  
    ```  
  
     Z oboma **— Vr** lub **— Vk** opcji, możesz opcjonalnie dołączyć plik .snk dla klucza podpisywania testów.  
  
    > [!WARNING]
    > Nie należy polegać na silne nazwy dla zabezpieczeń. Zapewniają one tylko unikatową tożsamość.
  
    > [!NOTE]
    >  Jeśli używasz opóźnione podpisywanie podczas programowania przy użyciu programu Visual Studio na komputerze 64-bitowym i kompilowania zestawu dla **dowolny Procesor**, może być konieczne zastosowanie **- Vr** opcji dwa razy. (W programie Visual Studio, **dowolny Procesor** jest wartością **platformę docelową** Tworzenie właściwości, podczas kompilowania z wiersza polecenia jest domyślna.) Aby uruchomić aplikację z poziomu wiersza polecenia lub Eksploratora plików, należy użyć 64-bitową wersję [Sn.exe (narzędzie silnych nazw)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) do zastosowania **- Vr** opcji do zestawu. Aby załadować zestaw do programu Visual Studio w czasie projektowania (na przykład, jeśli zestaw zawiera składniki, które są używane przez inne zestawy w aplikacji), użyj wersji 32-bitowe narzędzie silnych nazw. Jest to spowodowane kompilator just-in-time (JIT) kompiluje zestaw 64-bitowego kodu macierzystego przy uruchamianiu z wiersza polecenia zestawu i 32-bitowego kodu natywnego, gdy zestaw jest ładowany do środowiska czasu projektowania.  
  
5.  Później, zwykle po prostu przed wysyłką przesyłasz podpisywania urzędu dla rzeczywistego podpisywania silnymi nazwami przy użyciu zestawu dla Twojej organizacji **– R** opcji narzędzie silnych nazw.  
  
     Poniższy przykład podpisuje zestaw o nazwie `myAssembly.dll` z silną nazwą przy użyciu `sgKey.snk` pary kluczy.  
  
    ```  
    sn -R myAssembly.dll sgKey.snk  
    ```  
  
## <a name="see-also"></a>Zobacz też  
- [Tworzenie zestawów](../../../docs/framework/app-domains/create-assemblies.md)  
- [Instrukcje: tworzenie pary kluczy publiczny-prywatny](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)  
- [Sn.exe (narzędzie silnych nazw)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
- [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)
