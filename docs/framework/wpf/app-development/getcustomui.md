---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: a9c4c9d597f5cc1b172213d49a3dd5b8f1c1f671
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991377"
---
# <a name="getcustomui"></a>GetCustomUI
Wywoływane przez PresentationHost. exe w celu uzyskania niestandardowych postępów i komunikatów o błędach z hosta, jeśli zostały zaimplementowane.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzProgressAssemblyName`  
  
 określoną Wskaźnik do zestawu, który zawiera interfejs użytkownika postępu dostarczonego przez hosta.  
  
 `pwzProgressClassName`  
  
 określoną Nazwa klasy, która jest interfejsem użytkownika postępu dostarczonego przez hosta, najlepiej do [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] pliku z <xref:System.Windows.Controls.Page> jest elementem najwyższego poziomu. Ta klasa znajduje się w zestawie, który jest określony przez `pwzProgressAssemblyName`.  
  
 `pwzErrorAssemblyName`  
  
 określoną Wskaźnik do zestawu, który zawiera interfejs użytkownika o błędzie dostarczonym przez hosta.  
  
 `pwzErrorClassName`  
  
 określoną Nazwa klasy, która jest interfejsem użytkownika o błędzie dostarczonym przez hosta, najlepiej do pliku XAML z <xref:System.Windows.Controls.Page> jest jego elementem najwyższego poziomu. Ta klasa znajduje się w zestawie, który jest określony przez `pwzErrorAssemblyName`.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 WYNIK Ignorowane.  
  
## <a name="remarks"></a>Uwagi  
 Aplikacja hosta może mieć określony motyw, który PresentationHost. exe domyślne interfejsy użytkownika mogą nie być zgodne. W takim przypadku aplikacja hosta może zaimplementować [GetCustomUI](getcustomui.md) , aby zwracać interfejs użytkownika postępu i błędów do PresentationHost. exe. PresentationHost. exe zawsze będzie wywoływał [GetCustomUI](getcustomui.md) przed użyciem jego domyślnych interfejsów użytkownika.  
  
 Ta funkcja jest wywoływana raz podczas inicjowania PresentationHost.  
  
## <a name="see-also"></a>Zobacz także

- [IWpfHostSupport](iwpfhostsupport.md)
