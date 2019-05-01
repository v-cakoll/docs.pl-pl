---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: 30084143949d2243fd310448c52e6b861505ad66
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947969"
---
# <a name="getcustomui"></a>GetCustomUI
Metoda wywoływana przez PresentationHost.exe można pobrać niestandardowych postępu i komunikaty o błędach z hosta, jeśli zaimplementowana.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzProgressAssemblyName`  
  
 [out] Wskaźnik do zestawu, który zawiera interfejs użytkownika postępu dostarczone z hosta.  
  
 `pwzProgressClassName`  
  
 [out] Nazwa klasy, które jest dostarczone z hosta postępu interfejsu użytkownika, najlepiej [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] plik z <xref:System.Windows.Controls.Page> jest element najwyższego poziomu. Ta klasa znajduje się w zestawie, który jest określony przez `pwzProgressAssemblyName`.  
  
 `pwzErrorAssemblyName`  
  
 [out] Wskaźnik do zestawu, który zawiera interfejs użytkownika błędzie dostarczony przez hosta.  
  
 `pwzErrorClassName`  
  
 [out] Nazwa klasy, która jest użytkownikiem błędzie dostarczony host interfejsu najlepiej plik XAML z <xref:System.Windows.Controls.Page> jest element najwyższego poziomu. Ta klasa znajduje się w zestawie, który jest określony przez `pwzErrorAssemblyName`.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 HRESULT: Ignorowane.  
  
## <a name="remarks"></a>Uwagi  
 Aplikacja hosta może mieć określonych motyw, który interfejsy użytkownika domyślnego PresentationHost.exe firmy nie będą zgodne z. Jeśli jest to możliwe, aplikacja hosta można zaimplementować [getcustomui —](getcustomui.md) do zwrotu postęp oraz błąd interfejsy użytkownika PresentationHost.exe. Zawsze spowoduje wywołanie PresentationHost.exe [getcustomui —](getcustomui.md) przed rozpoczęciem korzystania z jego interfejsów użytkownika domyślnego.  
  
 Ta funkcja jest wywoływana jeden raz podczas inicjowania PresentationHost firmy.  
  
## <a name="see-also"></a>Zobacz także

- [IWpfHostSupport](iwpfhostsupport.md)
