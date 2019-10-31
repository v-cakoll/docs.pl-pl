---
title: 'Instrukcje: odwoływanie się do zestawu o silnej nazwie'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 427550e1fbeb38cefbb4afe97d80e198ac2d6cb0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127633"
---
# <a name="how-to-reference-a-strong-named-assembly"></a>Instrukcje: odwoływanie się do zestawu o silnej nazwie
Proces odwoływania się do typów lub zasobów w zestawie o silnej nazwie jest zwykle niewidoczny. Odwołanie można wykonać w czasie kompilacji (wczesne wiązanie) lub w czasie wykonywania.  
  
Odwołanie w czasie kompilacji odbywa się po wskazaniu kompilatora, który zestaw ma zostać skompilowany jawnie odwołuje się do innego zestawu. W przypadku korzystania z odwołania w czasie kompilacji kompilator automatycznie pobiera klucz publiczny do określonego zestawu o silnej nazwie i umieszcza go w odwołaniu do zestawu, który jest kompilowany.
  
> [!NOTE]
> Zestaw o silnej nazwie może używać tylko typów z innych zestawów o silnych nazwach. W przeciwnym razie zabezpieczenia zestawu o silnej nazwie byłyby naruszone.  
  
## <a name="make-a-compile-time-reference-to-a-strong-named-assembly"></a>Utwórz odwołanie w czasie kompilacji do zestawu o silnej nazwie  

W wierszu polecenia wpisz następujące polecenie:  

\<*polecenia kompilatora*>  **/Reference:** \<*Nazwa zestawu*>  

W tym poleceniu *kompilator* jest poleceniem kompilatora dla używanego języka, a *Nazwa zestawu* to nazwa zestawu o silnej nazwie. Można również użyć innych opcji kompilatora, takich jak opcja **/t: Library** do tworzenia zestawu biblioteki.  

Poniższy przykład tworzy zestaw o nazwie Moja *Assembly. dll* , który odwołuje się do zestawu o silnej nazwie o nazwie *myLibAssembly. dll* z modułu kodu o nazwie *myAssembly.cs*.  

```cmd
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  

## <a name="make-a-run-time-reference-to-a-strong-named-assembly"></a>Utwórz odwołanie w czasie wykonywania do zestawu o silnej nazwie  
  
Po wprowadzeniu odwołania w czasie wykonywania do zestawu o silnej nazwie, na przykład przy użyciu metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>, należy użyć nazwy wyświetlanej zestawu o silnej nazwie. Składnia nazwy wyświetlanej jest następująca:  

\<*nazwę zestawu*> **,** \<*numer wersji*> **,** \<>*kulturowe* **,** \<*token klucza publicznego*>  

Na przykład:  

```console
myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
```  

W tym przykładzie `PublicKeyToken` jest szesnastkową formą tokenu klucza publicznego. Jeśli nie ma żadnej wartości kulturowej, użyj `Culture=neutral`.  

Poniższy przykład kodu pokazuje, jak używać tych informacji przy użyciu metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.  

```cpp
Assembly^ myDll =
    Assembly::Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1");
```

```csharp
Assembly myDll =
    Assembly.Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1");
```

```vb
Dim myDll As Assembly = _
    Assembly.Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1")
```

Można wydrukować format szesnastkowy klucza publicznego i tokenu klucza publicznego dla określonego zestawu za pomocą następującego polecenia [silnej nazwy (SN. exe)](../../framework/tools/sn-exe-strong-name-tool.md) :  

**SN-Tp \<** *zestawu* **>**  

Jeśli masz plik klucza publicznego, możesz użyć poniższego polecenia (należy zwrócić uwagę na różnice w przypadku opcji wiersza polecenia):  

**SN-tp \<** *pliku klucza publicznego* **>**  

## <a name="see-also"></a>Zobacz także

- [Tworzenie i używanie zestawów o silnych nazwach](create-use-strong-named.md)
