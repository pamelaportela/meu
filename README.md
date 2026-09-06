# Pâmela
import math

# ==============================
# DADOS DO CENÁRIO B
# ==============================

V_linha = 230e3       # Tensão de linha [V]
I = 1655              # Corrente [A]
fp = 0.95             # Fator de potência
f = 60                # Frequência [Hz]


# ==============================
# 1. POTÊNCIA APARENTE
# ==============================

S = math.sqrt(3) * V_linha * I


# ==============================
# 2. POTÊNCIA ATIVA
# ==============================

P = S * fp


# ==============================
# 3. POTÊNCIA REATIVA
# ==============================

Q = S * math.sqrt(1 - fp**2)


# ==============================
# 4. ÂNGULO DA CARGA
# ==============================

phi = math.acos(fp)


# ==============================
# 5. TENSÃO DE FASE
# ==============================

V_fase = V_linha / math.sqrt(3)


# ==============================
# 6. IMPEDÂNCIA POR FASE
# ==============================

Z = V_fase / I


# ==============================
# 7. RESISTÊNCIA POR FASE
# ==============================

R = Z * fp


# ==============================
# 8. REATÂNCIA INDUTIVA
# ==============================

X_L = Z * math.sin(phi)


# ==============================
# 9. INDUTÂNCIA POR FASE
# ==============================

L = X_L / (2 * math.pi * f)


# ==============================
# RESULTADOS
# ==============================

print("===== DIMENSIONAMENTO DA CARGA - CENÁRIO B =====")

print(f"\nTensão de linha: {V_linha/1000:.2f} kV")
print(f"Corrente: {I:.2f} A")
print(f"Fator de potência: {fp:.2f} indutivo")

print("\n--- Potências ---")
print(f"Potência aparente: {S/1e6:.2f} MVA")
print(f"Potência ativa:    {P/1e6:.2f} MW")
print(f"Potência reativa:  {Q/1e6:.2f} MVAr")

print("\n--- Parâmetros por fase ---")
print(f"Tensão de fase:    {V_fase/1000:.2f} kV")
print(f"Impedância:        {Z:.2f} ohm")
print(f"Ângulo da carga:   {math.degrees(phi):.2f} graus")
print(f"Resistência R:     {R:.2f} ohm")
print(f"Reatância XL:      {X_L:.2f} ohm")
print(f"Indutância L:      {L*1000:.2f} mH")
