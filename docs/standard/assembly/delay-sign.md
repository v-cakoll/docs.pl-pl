---
title: Podpisywanie zestawu z opóźnieniem
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
ms.openlocfilehash: 113df1ad3fc3ac1e27ebfef572494c1f15a3dbb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73733163"
---
# <a name="delay-sign-an-assembly"></a>Podpisywanie zestawu z opóźnieniem

Organizacja może mieć ściśle strzeżoną parę kluczy, do których deweloperzy nie mogą uzyskać dostępu na co dzień. Klucz publiczny jest często dostępny, ale dostęp do klucza prywatnego jest ograniczony tylko do kilku osób. Podczas opracowywania zestawów o silnych nazwach, każdy zestaw, który odwołuje się do zestawu docelowego o silnej nazwie zawiera token klucza publicznego używanego do nadania zestawowi docelowemu silnej nazwy. Wymaga to, aby klucz publiczny był dostępny podczas procesu opracowywania.

Można użyć opóźnionego lub częściowego podpisywania w czasie kompilacji, aby zarezerwować miejsce w przenośnym pliku wykonywalnym (PE) dla podpisu silnej nazwy, ale odroczyć rzeczywiste podpisywanie do jakiegoś późniejszego etapu, zwykle tuż przed wysyłką zestawu.

Aby opóźnić-sign zestawu:

1. Pobierz część klucza publicznego pary kluczy od organizacji, która będzie wykonywać ostateczne podpisywanie. Zazwyczaj ten klucz jest w postaci pliku *.snk,* który może być utworzony przy użyciu [narzędzia Silna nazwa (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) dostarczonego przez zestaw Windows SDK.

2. Adnotuj kod źródłowy zestawu za <xref:System.Reflection>pomocą dwóch atrybutów niestandardowych z:

   - <xref:System.Reflection.AssemblyKeyFileAttribute>, który przekazuje nazwę pliku zawierającego klucz publiczny jako parametr do jego konstruktora.

   - <xref:System.Reflection.AssemblyDelaySignAttribute>, co wskazuje, że podpisywanie opóźnienia jest używany przez przekazywanie **true** jako parametr do jego konstruktora.

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

3. Kompilator wstawia klucz publiczny do manifestu zestawu i rezerwuje miejsce w pliku PE dla pełnego podpisu silnej nazwy. Prawdziwy klucz publiczny musi być przechowywany podczas złożenia jest zbudowany tak, aby inne zestawy, które odwołują się do tego zestawu można uzyskać klucz do przechowywania w ich odwołania do zestawu.

4. Ponieważ zestaw nie ma prawidłowego podpisu silnej nazwy, weryfikacja tego podpisu musi być wyłączona. Możesz to zrobić za pomocą opcji **-Vr** za pomocą narzędzia Silna nazwa.

     Poniższy przykład wyłącza weryfikację dla zestawu o nazwie *myAssembly.dll*.

   ```console
   sn –Vr myAssembly.dll
   ```

   Aby wyłączyć weryfikację na platformach, na których nie można uruchomić narzędzia Silna nazwa, takiego jak mikroprocesory ARM (Advanced RISC Machine), użyj opcji **–Vk,** aby utworzyć plik rejestru. Zaimportuj plik rejestru do rejestru na komputerze, na którym chcesz wyłączyć weryfikację. Poniższy przykład tworzy plik `myAssembly.dll`rejestru dla .

   ```console
   sn –Vk myRegFile.reg myAssembly.dll
   ```

   Za pomocą opcji **–Vr** lub **–Vk** można opcjonalnie dołączyć plik *.snk* do podpisywania klucza testowego.

   > [!WARNING]
   > Nie należy polegać na silne nazwy dla bezpieczeństwa. Zapewniają one tylko unikatową tożsamość.

   > [!NOTE]
   > Jeśli używasz podpisywania opóźnienia podczas tworzenia programu Visual Studio na komputerze 64-bitowym i skompilować zestaw dla **dowolnego procesora CPU,** może być trzeba zastosować opcję **-Vr** dwa razy. (W programie Visual Studio **dowolny procesor CPU** jest wartością właściwości kompilacji **docelowej platformy;** podczas kompilowania z wiersza polecenia jest to wartość domyślna). Aby uruchomić aplikację z wiersza polecenia lub z Eksploratora plików, użyj 64-bitowej wersji [narzędzia Sn.exe (Silna nazwa),](../../framework/tools/sn-exe-strong-name-tool.md) aby zastosować opcję **-Vr** do zestawu. Aby załadować zestaw do programu Visual Studio w czasie projektowania (na przykład jeśli zestaw zawiera składniki, które są używane przez inne zestawy w aplikacji), należy użyć 32-bitowej wersji narzędzia o silnej nazwie. Dzieje się tak, ponieważ kompilator just-in-time (JIT) kompiluje zestaw do 64-bitowego kodu macierzystego, gdy zestaw jest uruchamiany z wiersza polecenia, oraz do 32-bitowego kodu macierzystego po załadowaniu zestawu do środowiska czasu projektowania.

5. Później, zwykle tuż przed wysyłką, przesyłasz zestaw do urzędu podpisywania organizacji w celu podpisania rzeczywistej silnej nazwy za pomocą opcji **–R** za pomocą narzędzia Silna nazwa.

   Poniższy przykład podpisuje zestaw o nazwie *myAssembly.dll* o silnej nazwie przy użyciu pary *kluczy sgKey.snk.*

   ```console
   sn -R myAssembly.dll sgKey.snk
   ```

## <a name="see-also"></a>Zobacz też

- [Tworzenie zestawów](create.md)
- [Jak: Tworzenie pary kluczy publiczno-prywatnych](create-public-private-key-pair.md)
- [Sn.exe (narzędzie Silna nazwa)](../../framework/tools/sn-exe-strong-name-tool.md)
