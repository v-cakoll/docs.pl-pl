---
title: Podpisywanie zestawu z opóźnieniem
description: W tym artykule opisano opóźnione lub częściowe podpisywanie, które rezerwuje miejsce w pliku PE dla sygnatury silnej nazwy, ale postanowimy o faktycznym podpisywaniu.
ms.date: 08/19/2019
helpviewer_keywords:
- deferring assembly signing
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, delaying assembly signing
- partial assembly signing
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 7b5c8c8463fdc573782fa457bf5671c72a7e25f7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378502"
---
# <a name="delay-sign-an-assembly"></a>Podpisywanie zestawu z opóźnieniem

Organizacja może mieć dokładnie chronioną parę kluczy, której deweloperzy nie mogą uzyskać codziennie. Klucz publiczny jest często dostępny, ale dostęp do klucza prywatnego jest ograniczony tylko do kilku osób. Podczas tworzenia zestawów o silnych nazwach każdy zestaw, który odwołuje się do zestawu o silnej nazwie, zawiera token klucza publicznego, który jest używany do nadawania silnej nazwy zestawu docelowego. Wymaga to, aby klucz publiczny był dostępny podczas procesu tworzenia.

Możesz użyć opóźnionego lub częściowego podpisywania w czasie kompilacji, aby zarezerwować miejsce w przenośnym pliku wykonywalnym (PE) dla sygnatury silnej nazwy, ale odroczyć rzeczywiste podpisywanie do późniejszego etapu, zazwyczaj przed wysyłką zestawu.

Aby podpisać zestaw z opóźnieniem:

1. Pobierz część klucza publicznego pary kluczy z organizacji, która będzie podpisywać ostateczne. Zazwyczaj ten klucz jest w formie pliku *. snk* , który można utworzyć za pomocą [Narzędzia silnej nazwy (SN. exe)](../../framework/tools/sn-exe-strong-name-tool.md) dostarczonego przez Windows SDK.

2. Dodaj adnotację do kodu źródłowego dla zestawu z dwoma atrybutami niestandardowymi z <xref:System.Reflection> :

   - <xref:System.Reflection.AssemblyKeyFileAttribute>, który przekazuje nazwę pliku zawierającego klucz publiczny jako parametr do jego konstruktora.

   - <xref:System.Reflection.AssemblyDelaySignAttribute>, co oznacza, że jest używane podpisywanie opóźnień, przekazując **wartość true** jako parametr do jego konstruktora.

   Przykład:

   ```cpp
   [assembly:AssemblyKeyFileAttribute("myKey.snk")];
   [assembly:AssemblyDelaySignAttribute(true)];
   ```

   ```csharp
   [assembly:AssemblyKeyFileAttribute("myKey.snk")]
   [assembly:AssemblyDelaySignAttribute(true)]
   ```

   ```vb
   <Assembly:AssemblyKeyFileAttribute("myKey.snk")>
   <Assembly:AssemblyDelaySignAttribute(True)>
   ```

3. Kompilator wstawia klucz publiczny do manifestu zestawu i rezerwuje miejsce w pliku PE w celu uzyskania pełnej sygnatury silnej nazwy. Prawdziwy klucz publiczny musi być przechowywany podczas tworzenia zestawu, tak aby inne zestawy odwołujące się do tego zestawu mogły uzyskać klucz do przechowywania we własnym odwołaniu do zestawu.

4. Ponieważ zestaw nie ma prawidłowego podpisu silnej nazwy, weryfikacja tej sygnatury musi być wyłączona. Można to zrobić za pomocą opcji **– VR** za pomocą narzędzia silnej nazwy.

     Poniższy przykład wyłącza weryfikację dla zestawu o nazwie Moja *Assembly. dll*.

   ```console
   sn –Vr myAssembly.dll
   ```

   Aby wyłączyć weryfikację na platformach, w których nie można uruchomić narzędzia silnej nazwy, na przykład mikroprocesorów Advanced RISC Machine (ARM), użyj opcji **– VK** , aby utworzyć plik rejestru. Zaimportuj plik rejestru do rejestru na komputerze, na którym chcesz wyłączyć weryfikację. Poniższy przykład tworzy plik rejestru dla `myAssembly.dll` .

   ```console
   sn –Vk myRegFile.reg myAssembly.dll
   ```

   Za pomocą opcji **– VR** lub **– VK** można opcjonalnie dołączyć plik *. snk* do podpisywania klucza testowego.

   > [!WARNING]
   > Nie należy polegać na silnych nazwach zabezpieczeń. Zapewniają one tylko unikatową tożsamość.

   > [!NOTE]
   > Jeśli używasz opóźnienia podpisywania podczas opracowywania w programie Visual Studio na komputerze 64-bitowym i kompilujesz zestaw dla **dowolnego procesora**, może być konieczne dwukrotne zastosowanie opcji **-VR** . (W programie Visual Studio **każdy procesor CPU** jest wartością właściwości kompilacji **docelowej platformy** ; podczas kompilowania z wiersza polecenia jest to wartość domyślna). Aby uruchomić aplikację z poziomu wiersza polecenia lub Eksploratora plików, użyj 64-bitowej wersji [SN. exe (Narzędzie silnej nazwy)](../../framework/tools/sn-exe-strong-name-tool.md) , aby zastosować opcję **-VR** do zestawu. Aby załadować zestaw do programu Visual Studio w czasie projektowania (na przykład jeśli zestaw zawiera składniki, które są używane przez inne zestawy w aplikacji), użyj 32-bitowej wersji narzędzia silnej nazwy. Dzieje się tak, ponieważ kompilator just-in-Time (JIT) kompiluje zestaw do 64-bitowego kodu natywnego, gdy zestaw jest uruchamiany z wiersza polecenia i do 32-bitowy kod natywny, gdy zestaw jest ładowany do środowiska czasu projektowania.

5. Później, zazwyczaj tuż przed wysyłką, przesyłasz zestaw do urzędu podpisywania w organizacji w celu zapewnienia rzeczywistego podpisywania silnej nazwy przy użyciu opcji **– R** z narzędziem silnej nazwy.

   Poniższy przykład podpisuje zestaw o nazwie *plik. dll* o silnej nazwie przy użyciu pary kluczy *sgKey. snk* .

   ```console
   sn -R myAssembly.dll sgKey.snk
   ```

## <a name="see-also"></a>Zobacz też

- [Tworzenie zestawów](create.md)
- [Instrukcje: Tworzenie pary kluczy publiczny-prywatny](create-public-private-key-pair.md)
- [SN. exe (Narzędzie silnej nazwy)](../../framework/tools/sn-exe-strong-name-tool.md)
