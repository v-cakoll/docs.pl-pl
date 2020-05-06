---
title: Nieobsługiwane interfejsy API w programie .NET Core
titleSuffix: ''
description: Dowiedz się, które interfejsy API z .NET Framework, które zawsze zgłaszają wyjątek na platformie .NET Core.
ms.date: 12/23/2019
ms.openlocfilehash: 941e9149c7679afe4a888149108d0a9a28e5e7ab
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794601"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a>Interfejsy API, które zawsze generują wyjątki w programie .NET Core

Następujące interfejsy API zawsze będą zgłaszać <xref:System.PlatformNotSupportedException> na platformie .NET Core na wszystkich lub podzestawach platform.

Ten artykuł organizuje elementy członkowskie interfejsu API według przestrzeni nazw.

> [!NOTE]
>
> - Ten artykuł jest pracą w toku. Nie jest to kompletna lista interfejsów API, które generują wyjątki w programie .NET Core.
> - Ten artykuł nie zawiera jawnych implementacji interfejsu dla serializacji binarnej, która zgłasza na platformie .NET Core. Aby uzyskać więcej informacji, zobacz [Serializacja binarna w programie .NET Core](../../standard/serialization/binary-serialization.md#net-core).

## <a name="system"></a>System

| Członek | Platformy, które generują |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | Wszyscy |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | Wszyscy |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | Wszyscy |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | Wszyscy |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | Wszyscy |

## <a name="systemcodedomcompiler"></a>System. CodeDom. Compiler

| Członek | Platformy, które generują |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | Wszyscy |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | Wszyscy |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | Wszyscy |

## <a name="systemcollectionsspecialized"></a>System. Collections. specjalizowane

| Członek | Platformy, które generują |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Wszyscy |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | Wszyscy |

## <a name="systemconfiguration"></a>System. Configuration

| Członek | Platformy, które generują |
| - | - |
| <xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType>(wszystkie elementy członkowskie) | Wszyscy |

## <a name="systemconsole"></a>System. Console

| Członek | Platformy, które generują |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Console.BufferHeight?displayProperty=nameWithType>(tylko ustaw) | Linux i macOS |
| <xref:System.Console.BufferWidth?displayProperty=nameWithType>(tylko ustaw) | Linux i macOS |
| <xref:System.Console.CursorSize?displayProperty=nameWithType>(tylko ustaw) | Linux i macOS |
| <xref:System.Console.CursorVisible?displayProperty=nameWithType>(tylko pobieranie) | Linux i macOS |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Console.Title?displayProperty=nameWithType>(tylko pobieranie) | Linux i macOS |
| <xref:System.Console.WindowHeight?displayProperty=nameWithType>(tylko ustaw) | Linux i macOS |
| <xref:System.Console.WindowLeft?displayProperty=nameWithType>(tylko ustaw) | Linux i macOS |
| <xref:System.Console.WindowTop?displayProperty=nameWithType>(tylko ustaw) | Linux i macOS |
| <xref:System.Console.WindowWidth?displayProperty=nameWithType>(tylko ustaw) | Linux i macOS |

## <a name="systemdatacommon"></a>System. Data. Common

| Członek | Platformy, które generują |
| - | - |
| <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType>(zgłasza <xref:System.NotSupportedException>) | Wszyscy |

## <a name="systemdiagnosticsprocess"></a>System. Diagnostics. Process

| Członek | Platformy, które generują |
| - | - |
| <xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType>(tylko ustaw) | Linux |
| <xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType>(tylko ustaw) | Linux |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | macOS |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(tylko ustaw) | Linux i macOS |
| <xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(tylko pobieranie) | macOS |
| <xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType>(tylko ustaw) | Linux i macOS |

## <a name="systemio"></a>System.IO

| Członek | Platformy, które generują |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Wszyscy |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszyscy |

## <a name="systemiopipes"></a>System. IO. Pipes

| Członek | Platformy, które generują |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType>(tylko ustaw) | Linux i macOS |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | Linux i macOS |

## <a name="systemmedia"></a>System. Media

| Członek | Platformy, które generują |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Wszyscy |

## <a name="systemnet"></a>System.Net

| Członek | Platformy, które generują |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Wszyscy |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Wszyscy |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Wszyscy |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Wszyscy |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Wszyscy |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Wszyscy |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Wszyscy |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszyscy |

## <a name="systemnetnetworkinformation"></a>System .NET. NetworkInformation

| Członek | Platformy, które generują |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | Windows (platformy UWP) |

## <a name="systemnetsockets"></a>System .NET. Sockets

| Członek | Platformy, które generują |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | Wszyscy |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | Wszyscy |

## <a name="systemnetwebsockets"></a>System .NET. WebSockets

| Członek | Platformy, które generują |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | Wszyscy |

## <a name="systemreflection"></a>System. odbicie

| Członek | Platformy, które generują |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | Wszyscy |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Wszyscy |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | Wszyscy |

## <a name="systemruntimecompilerservices"></a>System. Runtime. CompilerServices

| Członek | Platformy, które generują |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | Wszyscy |

## <a name="systemruntimeinteropservices"></a>System. Runtime. InteropServices

| Członek | Platformy, które generują |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | Linux i macOS |

## <a name="systemruntimeserialization"></a>System.Runtime.Serialization

| Członek | Platformy, które generują |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | Wszyscy |

## <a name="systemsecurity"></a>System. Security

| Członek | Platformy, które generują |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | Wszyscy |

## <a name="systemsecurityclaims"></a>System. Security. Claims

| Członek | Platformy, które generują |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor> | Wszyscy |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | Wszyscy |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Wszyscy |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszyscy |

## <a name="systemsecuritycryptography"></a>System. Security. Cryptography

| Członek | Platformy, które generują |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | Wszyscy |

## <a name="systemsecuritycryptographypkcs"></a>System. Security. Cryptography. PKCS

| Członek | Platformy, które generują |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | Wszyscy |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | Wszyscy |

## <a name="systemsecuritycryptographyx509certificates"></a>System. Security. Cryptography. x509

| Członek | Platformy, które generują |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Wszyscy |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Wszyscy |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType>(tylko ustaw) | Wszyscy |

## <a name="systemsecurityauthenticationextendedprotection"></a>System. Security. Authentication. Kiedy

| Członek | Platformy, które generują |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Wszyscy |

## <a name="systemsecuritypolicy"></a>System. Security. Policy

| Członek | Platformy, które generują |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszyscy |

## <a name="systemserviceprocessservicecontroller"></a>System. ServiceProcess. ServiceController

| Członek | Platformy, które generują |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Wszyscy |

## <a name="systemtextregularexpressions"></a>System.Text.RegularExpressions

| Członek | Platformy, które generują |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | Wszyscy |

## <a name="systemthreading"></a>System. Threading

| Członek | Platformy, które generują |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | Wszyscy |

## <a name="systemxml"></a>System.Xml

| Członek | Platformy, które generują |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | Wszyscy |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | Wszyscy |

## <a name="see-also"></a>Zobacz także

- [Istotne zmiany dotyczące migracji z .NET Framework do platformy .NET Core](fx-core.md)
- [Serializacja binarna w programie .NET Core](../../standard/serialization/binary-serialization.md#net-core)
- [Analizator przenośności platformy .NET](../../standard/analyzers/portability-analyzer.md)
