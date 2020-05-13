---
title: 'Instrukcje: odwoływanie się do zestawu o silnej nazwie'
description: W tym artykule pokazano, jak odwoływać się do typów lub zasobów w przypadku zestawu o silnej nazwie .NET, w czasie kompilacji lub w środowisku uruchomieniowym.
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
ms.openlocfilehash: e42c1b461da16d7000605b9b9321138bbfebd307
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379874"
---
# <a name="how-to-reference-a-strong-named-assembly"></a>Instrukcje: odwoływanie się do zestawu o silnej nazwie
Proces odwoływania się do typów lub zasobów w zestawie o silnej nazwie jest zwykle niewidoczny. Odwołanie można wykonać w czasie kompilacji (wczesne wiązanie) lub w czasie wykonywania.  
  
Odwołanie w czasie kompilacji odbywa się po wskazaniu kompilatora, który zestaw ma zostać skompilowany jawnie odwołuje się do innego zestawu. W przypadku korzystania z odwołania w czasie kompilacji kompilator automatycznie pobiera klucz publiczny do określonego zestawu o silnej nazwie i umieszcza go w odwołaniu do zestawu, który jest kompilowany.
  
> [!NOTE]
> Zestaw o silnej nazwie może używać tylko typów z innych zestawów o silnych nazwach. W przeciwnym razie zabezpieczenia zestawu o silnej nazwie byłyby naruszone.  
  
## <a name="make-a-compile-time-reference-to-a-strong-named-assembly"></a>Utwórz odwołanie w czasie kompilacji do zestawu o silnej nazwie  

W wierszu polecenia wpisz następujące polecenie:  

\<*kompilator — polecenie* >  **/Reference:** \< *Nazwa zestawu*>  

W tym poleceniu *kompilator* jest poleceniem kompilatora dla używanego języka, a *Nazwa zestawu* to nazwa zestawu o silnej nazwie. Można również użyć innych opcji kompilatora, takich jak opcja **/t: Library** do tworzenia zestawu biblioteki.  

Poniższy przykład tworzy zestaw o nazwie Moja *Assembly. dll* , który odwołuje się do zestawu o silnej nazwie o nazwie *myLibAssembly. dll* z modułu kodu o nazwie *myAssembly.cs*.  

```cmd
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  

## <a name="make-a-run-time-reference-to-a-strong-named-assembly"></a>Utwórz odwołanie w czasie wykonywania do zestawu o silnej nazwie  
  
Podczas wykonywania odwołania do zestawu o silnej nazwie, na przykład przy użyciu <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> metody lub, należy użyć nazwy wyświetlanej zestawu o silnej nazwie. Składnia nazwy wyświetlanej jest następująca:  

\<*Nazwa zestawu* > **,** \< *numer wersji* > **,** \< *kultura* > **,** \< *token klucza publicznego*>  

Przykład:  

```console
myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33
```  

W tym przykładzie `PublicKeyToken` jest to szesnastkowa postać tokenu klucza publicznego. Jeśli nie ma żadnej wartości kulturowej, użyj `Culture=neutral` .  

Poniższy przykład kodu pokazuje, jak używać tych informacji przy użyciu <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.  

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

**SN-TP \< ** *zestaw***>**  

Jeśli masz plik klucza publicznego, możesz użyć poniższego polecenia (należy zwrócić uwagę na różnice w przypadku opcji wiersza polecenia):  

**SN-TP \< ** *plik klucza publicznego***>**  

## <a name="see-also"></a>Zobacz też

- [Tworzenie i używanie zestawów o silnej nazwie](create-use-strong-named.md)
