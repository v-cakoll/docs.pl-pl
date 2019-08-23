---
title: 'Instrukcje: Odwołanie do zestawu o silnej nazwie'
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
ms.openlocfilehash: 080d05a27b9e0b6ad4ff52d67ef8d9209dc1c697
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927955"
---
# <a name="how-to-reference-a-strong-named-assembly"></a>Instrukcje: Odwołanie do zestawu o silnej nazwie
Proces odwoływania się do typów lub zasobów w zestawie o silnej nazwie jest zwykle niewidoczny. Odwołanie można wykonać w czasie kompilacji (wczesne wiązanie) lub w czasie wykonywania.  
  
 Odwołanie w czasie kompilacji odbywa się po wskazaniu kompilatora, który zestaw jawnie odwołuje się do innego zestawu. W przypadku korzystania z odwołania w czasie kompilacji kompilator automatycznie pobiera klucz publiczny do określonego zestawu o silnej nazwie i umieszcza go w odwołaniu do zestawu, który jest kompilowany.  
  
> [!NOTE]
> Zestaw o silnej nazwie może używać tylko typów z innych zestawów o silnych nazwach. W przeciwnym razie zabezpieczenia zestawu o silnej nazwie byłyby naruszone.  
  
### <a name="to-make-a-compile-time-reference-to-a-strong-named-assembly"></a>Aby wykonać odwołanie do zestawu o silnej nazwie w czasie kompilacji  
  
1. W wierszu polecenia wpisz następujące polecenie:  
  
     \<*Kompilator polecenia*>  **/Reference:** \<*Nazwa zestawu*>  
  
     W tym poleceniu *kompilator* jest poleceniem kompilatora dla używanego języka, a *Nazwa zestawu* to nazwa zestawu o silnej nazwie. Można również użyć innych opcji kompilatora, takich jak opcja **/t: Library** do tworzenia zestawu biblioteki.  
  
 Poniższy przykład tworzy zestaw o nazwie `myAssembly.dll` , który odwołuje się do zestawu o silnej nazwie wywołanego `myLibAssembly.dll` z `myAssembly.cs`modułu kodu o nazwie.  
  
```  
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  
  
### <a name="to-make-a-run-time-reference-to-a-strong-named-assembly"></a>Aby wprowadzić odwołanie w czasie wykonywania do zestawu o silnej nazwie  
  
1. Podczas wykonywania odwołania do zestawu o silnej nazwie (na przykład przy użyciu <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody lub <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> ), należy użyć nazwy wyświetlanej zestawu o silnej nazwie. Składnia nazwy wyświetlanej jest następująca:  
  
     \<*Nazwa* zestawu,\< *numer wersji,* kultura, token klucza publicznego \<> \<>>>  
  
     Na przykład:  
  
    ```  
    myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
    ```  
  
     W tym przykładzie `PublicKeyToken` jest to szesnastkowa postać tokenu klucza publicznego. Jeśli nie ma żadnej wartości kulturowej, `Culture=neutral`Użyj.  
  
 Poniższy przykład kodu pokazuje, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> jak używać tych informacji przy użyciu metody.  
  
 [!code-cpp[Assembly.Load1#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.Load1/CPP/load2.cpp#3)]
 [!code-csharp[Assembly.Load1#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.Load1/CS/load2.cs#3)]
 [!code-vb[Assembly.Load1#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.Load1/VB/load2.vb#3)]  
  
 Można wydrukować format szesnastkowy klucza publicznego i tokenu klucza publicznego dla określonego zestawu za pomocą następującego polecenia [silnej nazwy (SN. exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) :  
  
 **SN — zestaw \< TP** **>**  
  
 Jeśli masz plik klucza publicznego, możesz użyć poniższego polecenia (należy zwrócić uwagę na różnice w przypadku opcji wiersza polecenia):  
  
 **SN-TP \< —** *plik klucza publicznego* **>**  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie i używanie zestawów o silnej nazwie](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
