---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: ff68c30c4e58cebb70c59352593d7b084413dce8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="getcustomui"></a>GetCustomUI
Metoda wywoływana przez PresentationHost.exe można pobrać niestandardowych postęp i komunikaty o błędach z hosta, jeśli zaimplementowane.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwzProgressAssemblyName`  
  
 [out] Wskaźnik do zestawu, który zawiera interfejs użytkownika postępu hosta dostarczone.  
  
 `pwzProgressClassName`  
  
 [out] Nazwa klasy, która najlepiej jest interfejs użytkownika postępu hosta dostarczone, [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] pliku z <xref:System.Windows.Controls.Page> jest jego element najwyższego poziomu. Ta klasa znajduje się w zestawie, który jest określony przez `pwzProgressAssemblyName`.  
  
 `pwzErrorAssemblyName`  
  
 [out] Wskaźnik do zestawu zawierającego hosta dostarczone błąd interfejsu użytkownika.  
  
 `pwzErrorClassName`  
  
 [out] Nazwa klasy, która jest użytkownikiem hosta dostarczone błąd interfejsu, najlepiej plik XAML z <xref:System.Windows.Controls.Page> jest jego element najwyższego poziomu. Ta klasa znajduje się w zestawie, który jest określony przez `pwzErrorAssemblyName`.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 Wynik HRESULT: ignorowane.  
  
## <a name="remarks"></a>Uwagi  
 Aplikacja hosta może mieć określonej motyw interfejsów użytkownika firmy PresentationHost.exe domyślny może nie być zgodne. Jeśli jest to możliwe, można wdrożyć aplikacji hosta [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) do zwrócenia postęp i błąd interfejsu użytkownika do PresentationHost.exe. Zawsze spowoduje wywołanie PresentationHost.exe [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) przed użyciem jej interfejsów użytkownika domyślnego.  
  
 Ta funkcja jest wywoływana raz podczas inicjowania PresentationHost firmy.  
  
## <a name="see-also"></a>Zobacz też  
 [IWpfHostSupport](../../../../docs/framework/wpf/app-development/iwpfhostsupport.md)
