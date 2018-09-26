---
title: 'Porady: odwołanie do zestawu o silnej nazwie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: abc53381bf6cc8458b83edf5586b76fe7ed5f303
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47088649"
---
# <a name="how-to-reference-a-strong-named-assembly"></a>Porady: odwołanie do zestawu o silnej nazwie
Proces odwołania do typów lub zasoby znajdujące się zestawu z silną nazwą jest zazwyczaj niewidoczny. Istnieje możliwość odwołania w czasie kompilacji (wczesne powiązania) lub w czasie wykonywania.  
  
 Odwołanie kompilacji występuje, gdy w kompilatorze wskazujesz, że zestaw jawnie odwoływać się do innego zestawu. Gdy używasz odwołujące się do kompilacji, kompilator automatycznie pobiera klucz publiczny zestawu o silnej nazwie docelowych i umieszcza je w zestawu kompilowanego odwołanie do zestawu.  
  
> [!NOTE]
>  Zestaw o silnej nazwie można używać tylko typów od innych zestawów o silnych nazwach. W przeciwnym razie zabezpieczeń zestawu o silnej nazwie może być narażone na ataki.  
  
### <a name="to-make-a-compile-time-reference-to-a-strong-named-assembly"></a>Kompilacji odwołać się do zestawu o silnej nazwie  
  
1.  W wierszu polecenia wpisz następujące polecenie:  
  
     \<*polecenie kompilatora*> **/reference:**\<*nazwy zestawu*>  
  
     W tym poleceniu *polecenia kompilatora* polecenia kompilatora dla języka, którego używasz, i *nazwy zestawu* to nazwa zestawu o silnej nazwie, do którego nastąpiło odwołanie. Umożliwia także inne opcje kompilatora, takich jak **/t** opcją w przypadku tworzenia zestawu biblioteki.  
  
 Poniższy przykład tworzy zestaw o nazwie `myAssembly.dll` odwołuje się zestaw o silnej nazwie, o nazwie `myLibAssembly.dll` moduł kodu o nazwie `myAssembly.cs`.  
  
```  
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  
  
### <a name="to-make-a-run-time-reference-to-a-strong-named-assembly"></a>Zapewnienie środowiska wykonawczego odwołanie do zestawu z silną nazwą  
  
1.  Po ustawieniu środowiska wykonawczego odwołanie do zestawu z silną nazwą (na przykład za pomocą <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> metoda), należy użyć nazwy wyświetlania przywoływanego zestawu o silnej nazwie. Składnia Nazwa wyświetlana jest następująca:  
  
     \<*Nazwa zestawu*>**,** \< *numer wersji*>**,** \< *kultury*  > **,** \< *token klucza publicznego*>  
  
     Na przykład:  
  
    ```  
    myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
    ```  
  
     W tym przykładzie `PublicKeyToken` jest szesnastkowe formą token klucza publicznego. Jeśli nie istnieje wartość kultury, należy użyć `Culture=neutral`.  
  
 Poniższy przykład kodu pokazuje, jak dzięki tym informacjom o <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.  
  
 [!code-cpp[Assembly.Load1#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.Load1/CPP/load2.cpp#3)]
 [!code-csharp[Assembly.Load1#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.Load1/CS/load2.cs#3)]
 [!code-vb[Assembly.Load1#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.Load1/VB/load2.vb#3)]  
  
 Można wydrukować szesnastkowej klucz publiczny i token klucza publicznego dla określonego zestawu przy użyciu następujących [silnych nazw (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) polecenia:  
  
 **SN - Tp \<**  *zestawu* **>**  
  
 Jeśli masz plik klucza publicznego, należy użyć następującego polecenia (należy zauważyć różnicę w przypadku opcji wiersza polecenia):  
  
 **SN - tp \<**  *pliku klucza publicznego* **>**  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie i używanie zestawów o silnej nazwie](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
