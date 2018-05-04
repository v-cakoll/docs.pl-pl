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
ms.openlocfilehash: 7f78fff50d1a227061076790ad77f17debe3f690
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-reference-a-strong-named-assembly"></a>Porady: odwołanie do zestawu o silnej nazwie
Proces odwołania do typów lub zasoby zestawu z silną nazwą jest zazwyczaj niewidoczny. Istnieje możliwość odwołania w czasie kompilacji (wczesne wiązanie) lub w czasie wykonywania.  
  
 Odwołanie kompilacji występuje, gdy w kompilatorze wskazaniu, że używanemu zestawowi jawnie odwoływać się do innego zestawu. Korzystając z odwołujące się do kompilacji, kompilator automatycznie pobiera klucz publiczny docelowego zestawu o silnej nazwie i umieszcza je w odwołaniu do zestawu jest kompilowane zestawu.  
  
> [!NOTE]
>  Zestaw o silnej nazwie można używać tylko typów od innych zestawów o silnych nazwach. W przeciwnym razie będzie naruszenia zabezpieczeń zestawu o silnej nazwie.  
  
### <a name="to-make-a-compile-time-reference-to-a-strong-named-assembly"></a>Kompilacji odwołać się do zestawu o silnej nazwie  
  
1.  W wierszu polecenia wpisz następujące polecenie:  
  
     \<*polecenie kompilatora*> **/reference:**\<*nazwy zestawu*>  
  
     W tym poleceniu *polecenia kompilatora* polecenia kompilatora języka używasz, i *nazwy zestawu* jest nazwą jest odwołanie do zestawu o silnej nazwie. Umożliwia także inne opcje kompilatora, takich jak **Library** opcja do tworzenia zestawu biblioteki.  
  
 Poniższy przykład tworzy zestaw o nazwie `myAssembly.dll` odwołuje się zestaw o silnej nazwie o nazwie `myLibAssembly.dll` z modułu kodu o nazwie `myAssembly.cs`.  
  
```  
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  
  
### <a name="to-make-a-run-time-reference-to-a-strong-named-assembly"></a>Do czasu wykonywania odwołać się do zestawu z silną nazwą  
  
1.  Po dokonaniu środowiska wykonawczego odwołanie do zestawu z silną nazwą (na przykład za pomocą <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> metodę), należy użyć nazwy wyświetlanej przywoływanego zestawu o silnej nazwie. Składnia nazwy wyświetlanej jest następujący:  
  
     \<*Nazwa zestawu*>**,** \< *numer wersji*>**,** \< *kultury*  > **,** \< *token klucza publicznego*>  
  
     Na przykład:  
  
    ```  
    myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
    ```  
  
     W tym przykładzie `PublicKeyToken` jest postaci szesnastkowej tokenu klucza publicznego. Jeśli nie ma żadnej wartości kultury, użyj `Culture=neutral`.  
  
 Poniższy przykład kodu pokazuje sposób używania tych informacji z <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.  
  
 [!code-cpp[Assembly.Load1#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.Load1/CPP/load2.cpp#3)]
 [!code-csharp[Assembly.Load1#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.Load1/CS/load2.cs#3)]
 [!code-vb[Assembly.Load1#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.Load1/VB/load2.vb#3)]  
  
 Można drukować szesnastkowej klucz publiczny i token klucza publicznego dla określonego zestawu przy użyciu następujących [Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) polecenia:  
  
 **SN - Tp \<**  *zestawu* **>**  
  
 Jeśli masz plik klucza publicznego, można użyć następującego polecenia (Uwaga różnica w przypadku opcji wiersza polecenia):  
  
 **SN - tp \<**  *zestawu* **>**  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie i używanie zestawów o silnej nazwie](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
