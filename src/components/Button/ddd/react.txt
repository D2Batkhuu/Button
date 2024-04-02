import React from 'react';
import './Button.css';

enum ButtonColor {
    Primary = 'primary',
    Secondary = 'secondary',
    Gray = 'gray',
    Destructive = 'destructive',
}

enum ButtonVariant {
    Filled = 'filled',
    Outlined = 'outlined',
    Text = 'text',
}

enum ButtonState {
    Default = 'default',
    Hover = 'hover',
    Focused = 'focused',
    Pressed = 'pressed',
    Disabled = 'disabled',
}

interface ButtonProps {
    label: string;
    color: ButtonColor;
    variant: ButtonVariant;
    state: ButtonState;
    size: 'small' | 'medium' | 'large';
    radius?: number; // Make the radius optional
}

const Button: React.FC<ButtonProps> = ({
    label,
    size,
    variant,
    color,
    state,
    radius = 8, // Default radius value
}: ButtonProps) => {
    const buttonClasses = [
        'button',
        `button-${size}`,
        `button-${color}-${variant}-${state}`,
        size === 'small' ? 'button-border-small' : '',
        size === 'medium' ? 'button-border-medium' : '',
        size === 'large' ? 'button-border-large' : '',
    ].join(' ');

    const style: React.CSSProperties = {
        borderRadius: radius + 'px',
    };

    return <button className={buttonClasses} style={style}>{label}</button>;
};

Button.defaultProps = {
    size: 'medium',
    variant: 'filled',
    state: 'default',
};

export default Button;
