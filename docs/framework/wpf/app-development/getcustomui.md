---
title: GetCustomUI
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f3c101ad13df9b99a2d872bac8783baed8b4b9a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
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
