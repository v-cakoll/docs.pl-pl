---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: e9ef32912c2afb3c99e46e1e14bb3daa5a2e99af
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005712"
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
  
 określoną Nazwa klasy, która jest interfejsem użytkownika postępu dostarczonego przez hosta, najlepiej plik XAML z <xref:System.Windows.Controls.Page> jest elementem najwyższego poziomu. Ta klasa znajduje się w zestawie, który jest określony przez `pwzProgressAssemblyName`.  
  
 `pwzErrorAssemblyName`  
  
 określoną Wskaźnik do zestawu, który zawiera interfejs użytkownika o błędzie dostarczonym przez hosta.  
  
 `pwzErrorClassName`  
  
 określoną Nazwa klasy, która jest interfejsem użytkownika o błędzie dostarczonym przez hosta, najlepiej do pliku XAML z <xref:System.Windows.Controls.Page> jest elementem najwyższego poziomu. Ta klasa znajduje się w zestawie, który jest określony przez `pwzErrorAssemblyName`.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 HRESULT: zignorowano.  
  
## <a name="remarks"></a>Uwagi  
 Aplikacja hosta może mieć określony motyw, który PresentationHost. exe domyślne interfejsy użytkownika mogą nie być zgodne. W takim przypadku aplikacja hosta może zaimplementować [GetCustomUI](getcustomui.md) , aby zwracać interfejs użytkownika postępu i błędów do PresentationHost. exe. PresentationHost. exe zawsze będzie wywoływał [GetCustomUI](getcustomui.md) przed użyciem jego domyślnych interfejsów użytkownika.  
  
 Ta funkcja jest wywoływana raz podczas inicjowania PresentationHost.  
  
## <a name="see-also"></a>Zobacz także

- [IWpfHostSupport](iwpfhostsupport.md)
