---
title: "CA2222: Do not decrease inherited member visibility | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.technology: 
  - "vs-ide-code-analysis"
ms.topic: "conceptual"
f1_keywords: 
  - "DoNotDecreaseInheritedMemberVisibility"
  - "CA2222"
helpviewer_keywords: 
  - "DoNotDecreaseInheritedMemberVisibility"
  - "CA2222"
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
author: "gewarren"
ms.author: "gewarren"
manager: douge
ms.workload: 
  - "multiple"
---
# CA2222: Do not decrease inherited member visibility
|||  
|-|-|  
|TypeName|DoNotDecreaseInheritedMemberVisibility|  
|CheckId|CA2222|  
|Category|Microsoft.Usage|  
|Breaking Change|Non Breaking|  
  
## Cause  
 A private method in an unsealed type has a signature that is identical to a public method declared in a base type. The private method is not final.  
  
## Rule Description  
 You should not change the access modifier for inherited members. Changing an inherited member to private does not prevent callers from accessing the base class implementation of the method. If the member is made private and the type is unsealed, inheriting types can call the last public implementation of the method in the inheritance hierarchy. If you must change the access modifier, either the method should be marked final or its type should be sealed to prevent the method from being overridden.  
  
## How to Fix Violations  
 To fix a violation of this rule, change the access to be non-private. Alternatively, if your programming language supports it, you can make the method final.  
  
## When to Suppress Warnings  
 Do not suppress a warning from this rule.  
  
## Example  
 The following example shows a type that violates this rule.  
  
 [!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
 [!code-csharp[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]