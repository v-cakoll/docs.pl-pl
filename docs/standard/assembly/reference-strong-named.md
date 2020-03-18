---
title: 'Jak: Odwoływać się do zestawu o silnej nazwie'
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
ms.openlocfilehash: adda4ed2ab5c59e3518b8e724044529a79840ad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156481"
---
# <a name="how-to-reference-a-strong-named-assembly"></a>Jak: Odwoływać się do zestawu o silnej nazwie
Proces odwoływania się do typów lub zasobów w zestawie o silnej nazwie jest zwykle przezroczysty. Odwołanie można dokonać w czasie kompilacji (wczesne powiązanie) lub w czasie wykonywania.  
  
Odwołanie w czasie kompilacji występuje, gdy wskażesz kompilatorowi, że zestaw, który ma zostać skompilowany, jawnie odwołuje się do innego zestawu. Korzystając z odwołania w czasie kompilacji, kompilator automatycznie pobiera klucz publiczny docelowego zestawu o silnej nazwie i umieszcza go w odwołaniu do zestawu kompilowanego zestawu.
  
> [!NOTE]
> Zestaw o silnej nazwie może używać tylko typów z innych zestawów o silnej nazwie. W przeciwnym razie bezpieczeństwo zestawu o silnej nazwie zostanie naruszone.  
  
## <a name="make-a-compile-time-reference-to-a-strong-named-assembly"></a>Nawiązywanie odwołania w czasie kompilacji do zestawu o silnej nazwie  

W wierszu polecenia wpisz następujące polecenie:  

\<*command /reference kompilator:*> **/reference:**\<*nazwa zestawu*>  

W tym *poleceniu polecenie kompilatora* jest poleceniem kompilatora dla języka, którego używasz, a *nazwa zestawu* jest nazwą zestawu o silnej nazwie, do którego się odwołuje. Można również użyć innych opcji kompilatora, takich jak **/t:library** opcja tworzenia zestawu biblioteki.  

Poniższy przykład tworzy zestaw o nazwie *myAssembly.dll,* który odwołuje się do zestawu o silnej nazwie o nazwie *myLibAssembly.dll* z modułu kodu o nazwie *myAssembly.cs*.  

```cmd
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  

## <a name="make-a-run-time-reference-to-a-strong-named-assembly"></a>Nawiązywanie odwołania w czasie wykonywania do zestawu o silnej nazwie  
  
Podczas odwoływania się do zestawu o silnej nazwie, na <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> przykład przy użyciu lub metody, należy użyć nazwy wyświetlanej zestawu o silnej nazwie. Składnia nazwy wyświetlanej jest następująca:  

\<*nazwa*>zestawu **,** \< *numer*>wersji **,** \< *kultura*>**,** \<token *klucza publicznego*>  

Przykład:  

```console
myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33
```  

W tym `PublicKeyToken` przykładzie jest szesnastkowafora tokenu klucza publicznego. Jeśli nie ma wartości `Culture=neutral`kultury, użyj .  

W poniższym przykładzie kodu pokazano, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> jak używać tych informacji z metodą.  

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

Format szesnastkowy klucza publicznego i tokenu klucza publicznego dla określonego zestawu można wydrukować przy użyciu następującego polecenia [Silna nazwa (Sn.exe):You](../../framework/tools/sn-exe-strong-name-tool.md) can print the sxadecimal format of the public key and public key token for a specific assembly using the following Strong Name (Sn.exe) command:  

**sn -Zespół Tp \< ** *assembly***>**  

Jeśli masz plik klucza publicznego, możesz użyć następującego polecenia (zwróć uwagę na różnicę w przypadku opcji wiersza polecenia):  

**sn -tp \< ** *plik klucza publicznego***>**  

## <a name="see-also"></a>Zobacz też

- [Tworzenie i używanie zestawów o silnej nazwie](create-use-strong-named.md)
