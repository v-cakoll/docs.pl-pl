---
title: "Lokalizacja działania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ee7bc16-e609-469a-a3e8-8062952e2676
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f7746e2ffc61db6d7863e243396f6d1bba315150
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="activity-localization"></a>Lokalizacja działania
Jeśli przepływ pracy aplikacji i składników może być zlokalizowana na innych kultur i języków, ciągów zasobów powinien być używany, dzięki czemu może być lokalizowany bez konieczności ponownego kompilowania.  
  
## <a name="activity-localization"></a>Lokalizacja działania  
 Jako z wszystkich aplikacji, które muszą być lokalizowany (wydane w różnych wersjach dla różnych języków i kultur), dowolne ciągi, które są wyświetlane użytkownikowi powinien nie można umieścić bezpośrednio w kodzie, ale raczej przechowywane w pliku zasobów. Następnie można możliwy ciągi za pośrednictwem <!--zz <xref:System.Environment.GetResourceString> --> `GetResourceString`. Jeśli tworzysz składnik, który jest dystrybuowane w różnych językach, należy użyć ciągów zasobów dla komunikatów dotyczących sprawdzania poprawności działania, zdefiniowane przez użytkownika śledzenia danych, komunikaty śledzenia i komunikaty o błędach oraz.  
  
 Poniższym ćwiczeniu przedstawiono sposób użycia pliku zasobu.  
  
#### <a name="using-resource-files-for-localized-strings"></a>Przy użyciu plików zasobów dla zlokalizowanych ciągów  
  
1.  W [!INCLUDE[vs2010](../../../includes/vs2010-md.md)], kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **Dodaj...** , **Nowy element...** .  
  
2.  Wybierz **pliku zasobów** i nazwij plik ErrorResources.resx. Kliknij przycisk **Dodaj**.  
  
3.  Otwórz plik zasobu. Dodaj nowy wpis o **nazwa** z ErrorString i **wartość** "działania nie jest prawidłowy."  
  
4.  Dodaj następujące `using` instrukcje do swojej klasy.  
  
    ```  
    using System.Reflection;  
    using System.Resources;  
    ```  
  
5.  Utwórz zasób menedżera w projekcie.  
  
    ```  
    ResourceManager ErrorManager;  
    ...  
    ErrorManager = new ResourceManager("MyNamespace.ErrorResources", Assembly.GetExecutingAssembly());  
    ```  
  
6.  Pobrać ciąg Menedżera zasobów, w których jest wymagane.  
  
    ```  
    String errorMessage = ErrorManager.GetString("ErrorString");  
    ```  
  
 Poniższy przykład kodu pokazuje, jak korzystać z zlokalizowanych ciągów w <xref:System.Activities.Activity.CacheMetadata%2A> metody.  
  
```  
       protected override void CacheMetadata(CodeActivityMetadata metadata)  
        {  
           .....  
          // rest of the code elided for brevity  
           .....  
            if (this.Value != null && this.To != null)  
            {  
                if (!TypeHelper.AreTypesCompatible(this.Value.ArgumentType, this.To.ArgumentType))  
                {  
//---------------------------------------------  
// ** SR.TypeMismatchForAssign will fetch the string from the resource manager **  
//---------------------------------------------  
                    metadata.AddValidationError(SR.TypeMismatchForAssign(  
                                this.Value.ArgumentType,  
                                this.To.ArgumentType,  
                                this.DisplayName));  
                }  
            }  
        }  
```
